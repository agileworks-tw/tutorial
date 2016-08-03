# 搭配 JUnit 進行 Rest API 測試

在進行 API 測試時，會有兩個部分，一個是專案本身為 API server，我們希望可以對 API 的 request 與 response 進行驗證。

一則是需要驗證第三方 API，比如 Facebook 或是 Google 所提供的權限驗證的 API 則是另外一個情境，此章節將針對兩個情形進行說明與演練。

## server api 測試，以 Spring-boot 為例

若是 Server 內部 API 測試，會根據使用的 Framework 有所不同，此範例使用 Spring-boot。

### 參考範例

<https://github.com/agileworks-tw/spring-boot-sample/blob/master/src/test/java/sample/data/rest/SampleDataRestApplicationTests.java>

### 測試案例

透過 `this.mvc = MockMvcBuilders.webAppContextSetup(this.context).build();` 啟動 server
透過 `this.mvc.perform` 來對 API 進行存取

```java
@RunWith(SpringJUnit4ClassRunner.class)
@SpringApplicationConfiguration(SampleDataRestApplication.class)
@WebAppConfiguration
@ActiveProfiles("scratch") //此行將載入 src/test/resources/application-scratch.properties
// Separate profile for web tests to avoid clashing databases
public class SampleDataRestApplicationTests {

	@Autowired
	private WebApplicationContext context;

	private MockMvc mvc;

	@Before
	public void setUp() {
		//mock api server
		this.mvc = MockMvcBuilders.webAppContextSetup(this.context).build();
	}

	@Test
	public void testHome() throws Exception {

		this.mvc.perform(get("/api")).andExpect(status().isOk())
				.andExpect(content().string(containsString("hotels")));
	}

	@Test
	public void findByNameAndCountry() throws Exception {

		this.mvc.perform(
				get("/api/cities/search/findByNameAndCountryAllIgnoringCase?name=Melbourne&country=Australia"))
				.andExpect(status().isOk())
				.andExpect(jsonPath("state", equalTo("Victoria")))
				.andExpect(jsonPath("name", equalTo("Melbourne")));
	}

	@Test
	public void findByContaining() throws Exception {

		this.mvc.perform(
				get("/api/cities/search/findByNameContainingAndCountryContainingAllIgnoringCase?name=&country=UK"))
				.andExpect(status().isOk())
				.andExpect(jsonPath("_embedded.cities", hasSize(3)));
	}
}
```


## 測試第三方 API

### 參考範例

<https://github.com/agileworks-tw/spring-boot-sample/blob/master/src/test/java/sample/data/rest/SampleDataRestApplicationTests.java>

### 測試案例

以原 Sample 為例，測試步驟

1. 透過 `spring-boot:run` 來啟動 server
2. 執行 `mvn -Dtest=ThirdPartyApiTest test` 進行測試

這樣的測試方式通常會用於 TDD 剛開始導入時，先針對 API 進行驗證，也比較容易進行，缺點是因為是外部執行測試，所以自動化測試上步驟較繁瑣。

另外一種情形為 API 不屬於我們的維護範圍，為了確保第三方 API 運作正常，也就不得不使用次方式進行測試

``` java
package sample.data.rest;
import org.json.JSONObject;
import org.junit.Test;
import org.springframework.web.client.RestTemplate;
import static org.assertj.core.api.Assertions.assertThat;


public class ThirdPartyApiTest {

    final RestTemplate template = new RestTemplate();

    @Test
    public void testCitiesSearch() throws Exception {
        String api = "http://localhost:8000/api/cities/search/findByNameAndCountryAllIgnoringCase";
        String params = "?name=Melbourne&country=Australia";
        String url = api + params;

        String message = template.getForObject(url, String.class);
        JSONObject jsonObj = new JSONObject(message);
        assertThat(jsonObj.has("country")).isTrue();
    }
}

```
