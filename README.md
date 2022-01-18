# Rush + SST Playground

This repo is inspired by https://github.com/electblake/rushstack-sst-playground

- https://docs.serverless-stack.com/
- https://rushjs.io/
- https://rushstack.io/

## Init

Install rush:
```sh
$ npm install -g @microsoft/rush
```

This repo was created with `rush init`.

After cloning the repo, run `rush setup` and `rush install`.

## Create SST project

```sh
$ cd apps
$ pnpx create-serverless-stack@latest --language typescript rest-api-ts
```

The SST script will still use NPM for installing dependencies, so the `package-lock.json` file must
be deleted together with the `node_modules` folder.

Add the new project to the `rush.json` file under the `projects` section:
```json
    {
      "packageName": "rest-api-ts",
      "projectFolder": "apps/rest-api-ts"
    }
```

Run `rush update` to recreate the `node_modules` folder and resolve dependencies.

### Build and deploy SST project

Development with debug stack deployed on AWS:
```sh
$ cd apps/rest-api-ts

$ rushx build

$ rushx test

$ rushx start

$ rushx remove
```

Deploy/undeploy prod stage on AWS:
```sh
$ rushx deploy --stage prod

$ rushx diff --stage prod

$ rushx remove --stage prod
```
