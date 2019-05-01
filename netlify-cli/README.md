# netlify-cli

## Build
```
cd docker-helpers/netlify-cli/

docker build -t maxivanov/netlify-cli .
```

## Use
```
cd my-project/

docker run --rm -it -v $(pwd):/var/app -w /var/app maxivanov/netlify-cli netlify init --manual
```