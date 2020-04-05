# Helm Charts Repository

To add charts and update `index.yaml`:
1. `git clone git@github.com:mkorejo/helm_charts.git && cd helm_charts`
1. `helm package src/<my-chart> -d ./releases`
1. `helm repo index charts_repo --url https://mkorejo.github.io/charts_repo/`
1. Push up the chart package(s) and `index.yaml`