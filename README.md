# Docker Image for Running tests which require chrome

## Installed Tools

- git
- pip
- chrome
- node
- npm
- yarn

## For Google Cloud build

in cloudbuild.yaml file

```yaml
- name: 'gcr.io/$PROJECT_ID/chrome-node-yarn'
  args: ['run', 'test']
```

### For Karma

Note: Don't forget to make necessary changes in `karma.conf.js` file.

```yaml
- name: 'gcr.io/$PROJECT_ID/chrome-node-yarn'
  args:
    [
      'run',
      'test',
      '--',
      '--no-watch',
      '--no-progress',
      '--browsers=ChromeHeadlessNoSandbox',
    ]
```

### For Protractor

Note: Don't forget to create `protractor-ci.conf.js` in e2e folder.

```yaml
- name: 'gcr.io/$PROJECT_ID/chrome-node-yarn'
  args: ['run', 'e2e', '--', '--protractor-config=e2e/protractor-ci.conf.js']
```
