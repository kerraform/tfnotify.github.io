# GitHub Actions

Using [KeisukeYamashita/setup-release](https://github.com/KeisukeYamashita/setup-release) GitHub Action, installing tfnotify in your workflow will be very easy.

Add the job below:

```yaml
on: pull_request
jobs:
  provision-tagged-release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: KeisukeYamashita/setup-release@master
        with:
          repository: kerraform/tfnotify
      - name: Check version 
        run: tfnotify version
```

You can use the `tfnotify` in your following jobs.

## Specify version

You can specify version with `tag` argument like below:

```yaml  
steps:
    - uses: actions/checkout@v2
    - uses: KeisukeYamashita/setup-release@master
      with:
        repository: kerraform/tfnotify
        tag: v0.1.0
```

See all the releases in [this page](https://github.com/kerraform/tfnotify/releases).
