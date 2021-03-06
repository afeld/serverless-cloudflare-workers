# serverless-cloudflare-workers
Serverless plugin for Cloudflare Workers 

## Documentation

https://serverless.com/framework/docs/providers/cloudflare/guide/quick-start/

### Bundling with Webpack

You can have the plugin automatically bundle your code into one file using webpack. This is a great solution if you are fine with a no frills bundling.

Simply add webpack: true to your config block.

```
functions:
  myfunction:
    name: myfunction
    webpack: true
    script: handlers/myfunctionhandler
    events:
      - http:
          url: example.com/myfunction
          method: GET
  
```

### Using Cloudflare KV Storage

The plugin can create and bind a KV Storage namespace for your function by simpling adding a resources section.

The following will create a Namespace called "BEST_NAMESPACE" and bind the variable "TEST" to that namespace inside myfunction.

```
functions:
  myfunction:
    name: myfunction
    webpack: true
    script: handlers/myfunctionhandler
    resources:
      storage:
        - variable: TEST
          namespace: BEST_NAMESPACE
    events:
      - http:
          url: example.com/myfunction
          method: GET
```