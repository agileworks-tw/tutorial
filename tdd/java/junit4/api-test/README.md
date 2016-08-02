# 搭配 JUnit 進行 Rest API 測試

參考範例

https://github.com/agileworks-tw/spring-boot-sample/blob/master/src/test/java/sample/data/rest/SampleDataRestApplicationTests.java

```java
@RunWith(SpringJUnit4ClassRunner.class)
@SpringApplicationConfiguration(SampleDataRestApplication.class)
@WebAppConfiguration
@ActiveProfiles("scratch")
// Separate profile for web tests to avoid clashing databases
public class SampleDataRestApplicationTests {

	@Autowired
	private WebApplicationContext context;

	private MockMvc mvc;

	@Before
	public void setUp() {
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
