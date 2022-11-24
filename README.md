
![weatherhere](https://ik.imagekit.io/jabedzaman/Portfolio/image1_Wn_Po8SNi.png?ik-sdk-version=javascript-1.4.3&updatedAt=1669312117819)

# Weather Here

Check the weather in your city. Just input the city name and press enter !!! Thats all!!

## Run Locally

Clone the project

```bash
  git clone git@github.com:jabedzaman/weatherhere.git
```

Go to the project directory

```bash
  cd weatherhere
```

Install dependencies

```bash
  pnpm install
```

Start the server

```bash
  pnpm run serve
```


## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`VUE_APP_OPEN_WEATHER_API_KEY`

`VUE_APP_OPEN_WEATHER_API_URL`

`VUE_APP_API_KEY`


## Deployment

To deploy this project run

```bash
  sudo pnpm i -g vercel
  vercel login
  vercel
```

