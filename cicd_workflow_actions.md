Sure, here's a basic `.github/workflows/ci.yml` file that leverages your existing `package.json` scripts for deployment:

```yaml
name: CI/CD with Vitest

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Install dependencies
        run: npm install

      - name: Build for deployment
        run: npm run build

      - name: Deploy to GitHub Pages
        uses: actions/deploy-with-push@v3
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          branch: gh-pages # You might need to adjust this branch name
          folder: dist # Assuming your built files are in this directory
          push: true

```

**Explanation of the file:**

* **name**: This defines the name of your workflow for better identification.
* **on**: This section specifies when the workflow should be triggered. Here, it runs on push events to the `main` branch. You can adjust this to fit your needs.
* **jobs**: This defines the jobs within the workflow. Here, we have one job named `build-and-deploy`.
* **runs-on**: This specifies the runner environment where the job executes. Here, it uses an Ubuntu virtual machine.
* **steps**: This defines the individual steps within the job.
    * The first step checks out your code from the GitHub repository.
    * The second step installs dependencies using `npm install`.
    * The third step runs the `npm run build` script defined in your `package.json` to build your application.
    * The fourth step deploys the built application to GitHub Pages. It uses the `actions/deploy-with-push@v3` action, which requires a GitHub token (stored as a secret). You'll need to configure this secret within your GitHub repository settings.
        * `branch`: This specifies the branch where the built files are deployed. The default in this example is `gh-pages`, but you might use a different branch for deployment.
        * `folder`: This specifies the directory containing the built files to be deployed. Here, it assumes your built files are in the `dist` folder as defined in your `package.json` script.
        * `push`: This sets to `true` to automatically push the changes to the deployment branch after building.

**Important notes:**

* Make sure you replace `gh-pages` with the actual branch name you use for deployment if it's different.
* You'll need to configure the `GITHUB_TOKEN` secret within your GitHub repository settings for the deployment action to work. Refer to GitHub Actions documentation for details on creating secrets: [https://docs.github.com/actions/security-guides/encrypted-secrets](https://docs.github.com/actions/security-guides/encrypted-secrets).

This is a basic example. You can customize the workflow further based on your needs. For instance, you might want to add a step to run your Vitest tests before deployment or configure different deployment environments.
