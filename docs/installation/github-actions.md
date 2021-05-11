# GitHub Actions

Using [kerraform/setup-tfnotify](https://github.com/kerraform/setup-tfnotify) GitHub Action, installing tfnotify in your workflow will be very easy.

Add the job below:

```yaml
on: pull_request
jobs:
  provision-tagged-release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: kerraform/setup-tfnotify@v1.0.0
        with:
          tag: v0.1.0
      - name: Check version 
        run: tfnotify version
```

You can use the `tfnotify` in your following jobs.
If you want to install the latest version of tfnotify, you can remove the `with.tag` field.
