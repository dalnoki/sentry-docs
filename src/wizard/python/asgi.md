---
name: ASGI
doc_link: https://docs.sentry.io/platforms/python/guides/asgi/
support_level: production
type: framework
---

The ASGI middleware can be used to instrument any [ASGI](https://asgi.readthedocs.io/en/latest/)-compatible web framework to attach request data for your events.

This can be used to instrument, for example [Starlette](https://www.starlette.io/middleware/) or [Django Channels 2.0](https://channels.readthedocs.io/en/latest/).

```python
import sentry_sdk
from sentry_sdk.integrations.asgi import SentryAsgiMiddleware

from myapp import asgi_app

sentry_sdk.init(
    dsn="___PUBLIC_DSN___",

    # Set traces_sample_rate to 1.0 to capture 100%
    # of transactions for performance monitoring.
    # We recommend adjusting this value in production,
    traces_sample_rate=1.0,
)

asgi_app = SentryAsgiMiddleware(asgi_app)
```

The middleware supports both ASGI 2 and ASGI 3 transparently.

<!-- TODO-ADD-VERIFICATION-EXAMPLE -->
