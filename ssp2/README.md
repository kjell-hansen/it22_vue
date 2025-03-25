# ssp2 - Rock paper scissors, extended version

## Prerequisits
Install [node](https://nodejs.org/en/download/) Version 22 LTS.

Check your install with node -v && npm -v


## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

This will generate them into `dist` folder.

### An example for serving static files:

Use npm package called serve to serve the project in port 5000:

```sh  
install: npm install -g serve 
serve: serve -s -l 8080 dist
```
Test that the project is running by going to http://localhost:8080
