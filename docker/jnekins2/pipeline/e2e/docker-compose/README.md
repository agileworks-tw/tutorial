# 完整 docker-compose

```
version: '2'
services:
  build:
    container_name: sailsSample_dev
    image: agileworks/sails_sample_env
    command: "npm install"
    ports:
      - "5001:5001"
    working_dir: /sailsSample
    volumes:
      - ./:/sailsSample

  test:
    container_name: debug
    image: agileworks/sails_sample_env
    command: "npm run test-e2e-docker"

    expose:
      - "1338"
    ports:
      - "5001:5001"

    working_dir: /sailsSample
    volumes:
      - ./:/sailsSample
    depends_on:
      - "e2e-env"
    networks:
      - front-tier

  dev:
    container_name: sailsSample_dev
    image: agileworks/sails_sample_env
    command: "npm start"

    ports:
      - "5001:5001"

    working_dir: /sailsSample
    volumes:
      - ./:/sailsSample

  e2e-env:
    container_name: e2e-env
    image: selenium/standalone-firefox-debug:2.53.0
    expose:
      - "4444"
    ports:
      - "5900:5900"
    networks:
      - front-tier

networks:
  front-tier:
    driver: bridge
```
