# Build

## For Development (with git hash)
```
# run from root of selenium_demo_app repo
APP_VERSION=$(grep version default/app.conf | cut -d = -f 2 | sed -Ee 's/^( )+//g' -e 's/( )+$//g') \
  && COMMIT_HASH=$(git log -1 --pretty=format:%h) \
  && sed -E "s/^(version *=[^+]*)(\+.+)?/\1+${COMMIT_HASH}/" -i default/app.conf \
  && tar czf ../selenium_demo_app-${APP_VERSION}+${COMMIT_HASH}.tar.gz -C .. \
  --exclude-backups --exclude-vcs --exclude=local \
  selenium_demo_app
```
