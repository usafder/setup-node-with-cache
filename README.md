# Setup Node with Cache

GitHub action to efficiently set up your project that is using the node environment. You now don't have to write down all those boring steps for setting up your project as this action will take care of that for you!

> Note: Currently, it only supports `npm` but the idea is to add in support for other package managers like `yarn` and `pnpm` as well in the near future.

### Example Usage:
```yaml
name: CI
on:
  push:
    branches:
      - main

jobs:
  lint-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: usafder/setup-node-with-cache@v1.0.0
      - run: npm run lint
      - run: npm run test
```

As you can see in the example above, your workflow will become way too simpler now because you don't have to worry about defining all those steps like checking out the repo, setting up node or even downloading the dependencies as this action will handle all that for you. You now only need to define the steps that are to be executed after the installation of the dependencies.

By default it uses the node version of `18.0.0` but in case you wanna use a specific version of node (for eg. `18.14.2`) then you can do so by defining the node version in your project's `.nvmrc` file like this:
```
18.14.2
```

OR

provide the `NODE_VERSION` input to this action as shown below:
```yaml
name: CI
on:
  push:
    branches:
      - main

jobs:
  lint-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: usafder/setup-node-with-cache@v1.0.0
        with:
          NODE_VERSION: 18.14.2
      - run: npm run lint
      - run: npm run test
```
