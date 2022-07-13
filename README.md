# template-chart-go-cobra-app
Template repository for a helm chart for a golang cobra cli application with
configuration via viper

## Getting started

This helm template should work out of the box with the
[template-go-cobra-app](https://github.com/catalystsquad/template-go-cobra-app).
Before getting started with the helm chart, you should start your new project
off of the `template-go-cobra-app` template repository. Once you have your
project ready to go and publishing your container image to some repository, you
should be good to start making use of this helm template repository.

### The minimum updates required to get started

The only required change to the helm chart to get started is to update the
image reference to point to where you publish your new app image in
the [`values.yaml`](chart/values.yaml) file:
```yaml
image:
  repository: my-org/my-image-name # <- update this
```

### Initial customizations

Update the template for your new app name. You can use a find and replace
feature in your IDE or you can use the provided command to help you do so in a
Linux shell:
```sh
find chart/ -name '*.yaml' -or -name '*.txt' -or -name '*.tpl' | xargs sed -i 's/template-go-cobra-app/my-app-name/'
```

Update the [`CODEOWNERS`](.github/CODEOWNERS) and
[`settings.yml`](.github/settings.yml) files to ensure that your repo is
configured as desired. The `settings.yml` file is used by the [settings
app](https://github.com/apps/settings), which you will need to have installed
if you want to make use of it.


### Next steps

Now that you have a helm chart that works with the `template-go-cobra-app`, you
can now add any customization to the helm chart for your new app, here are some
recommended configuration next steps:

- Update the Chart.yaml with a description
- Remove any resource configuration that your app won't need, such as
  http-proxy or hpa if your app won't be designed to need those extra resources
- Update environment variable or argument configuration for any new input your
  app needs
- Add readiness checks if your app will need time before receiving traffic

