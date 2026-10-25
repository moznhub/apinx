# Examples

Ready-made definitions to copy, import and adapt. Every file is `apinx/v1` YAML or a Postman
collection, and every field is explained in the
[gateway configuration reference](https://apinx.io/docs/reference/GATEWAY-CONFIG/) and the
[policy reference](https://apinx.io/docs/reference/POLICIES/).

## Using them

- **`kind: API`**: open **Develop › APIs › New API › Code**, paste the file, save, then
  **Review and deploy**.
- **`kind: Gateway`** and **`kind: Upstream`**: import and publish from the terminal:

  ```bash
  apinxctl import examples/apis/upstream-resilient.yaml
  apinxctl publish -m "orders upstream"
  ```

  Or use **Admin › Import & export** in the console.

## API definitions

| File | What it shows |
|---|---|
| [`apis/upstream-resilient.yaml`](apis/upstream-resilient.yaml) | A backend with three targets, health checks, a circuit breaker and retries |
| [`apis/orders-api-key.yaml`](apis/orders-api-key.yaml) | API key, a rate limit per application, one public operation |
| [`apis/orders-jwt-cors.yaml`](apis/orders-jwt-cors.yaml) | JWT from your identity provider, CORS for a browser app, a jq response program |
| [`apis/product-with-plans.yaml`](apis/product-with-plans.yaml) | A product with a trial plan and a partner plan that needs approval |
| [`apis/security-baseline.yaml`](apis/security-baseline.yaml) | Global defaults and locked flow hooks every API runs |

More in [YAML samples](https://apinx.io/docs/guides/yaml-samples/).

## Postman collections

| Folder | What it shows |
|---|---|
| [`postman/`](postman/) | Calls [JSONPlaceholder](https://jsonplaceholder.typicode.com) through an API with an API key, a rate limit, jq reshaping and caching. Set `baseUrl` and `apiKey` first |
| [`hr-mobile/`](hr-mobile/) | A complete mobile backend: a three-step login with RS256 tokens, rate limits per address and per user, masked phone numbers, photo uploads and caching. The definition and a collection that tests every rule. Walkthrough: [A mobile backend, end to end](https://apinx.io/docs/tutorials/mobile-backend/) |

You can also bring your own APIs: import an OpenAPI document or a Postman collection (v2.0 or
v2.1) under **Admin › Import & export**. See
[Importing a Postman collection](https://apinx.io/docs/guides/postman-import/).
