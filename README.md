# amplify-vite

### How to build this Vite application locally:

- $ npm create vite@latest and follow the prompts!
- $ npm install
- $ npm run dev (local build)
- $ npm run build (production build)
- Notice that the build artifacts are generated under the `dist` directory

### How to build and deploy this Vite application on Amplify Hosting:

- Push the app's code to a git repository
- Connect the git repository to an Amplify app and during the app creation workflow edit the buildSpec (amplify.yml) file and set the baseDirectory to `dist`:

```
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm ci
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: dist
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```

- Once this is done, the build and deploy process should complete successfully.

[![amplifybutton](https://oneclick.amplifyapp.com/button.svg)](https://console.aws.amazon.com/amplify/home#/deploy?repo=https://github.com/Jay2113/amplify-vite)
