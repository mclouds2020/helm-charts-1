# Helm Charts Repository

To add charts and update `index.yaml`:
1. Clone this repo
1. Package your Helm chart with `helm package <local-path-to-chart>`
1. `mv` the packaged chart to your `charts_repo` clone
1. `helm repo index charts_repo --url https://mkorejo.github.io/charts_repo/`
1. Push up the chart package(s) and `index.yaml`