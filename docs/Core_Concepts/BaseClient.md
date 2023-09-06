# BaseClient: The Heart of DeclarativeX ❤️

## Introduction

Hey, welcome to the `BaseClient` section! If you're wondering what makes DeclarativeX tick, you've come to the right
place. `BaseClient` is the core class that powers all the magic. Let's dive in!

## Initialization

First things first, let's see how to initialize a `BaseClient`:

```{.python title="my_client.py"}
from declarativex import BaseClient

class MyClient(BaseClient):
    pass
```

That's it! You've just created your first `BaseClient`. 🎉

## Attributes

### `base_url`

The `base_url` is where all the magic starts. It's the root URL that your client will use for all requests.

=== "Using class attribute"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    class MyClient(BaseClient):
        base_url = "https://api.example.com"


    client = MyClient()
    ```
    !!! tip
        Prefer this approach if you don't need to change the `base_url` at runtime.

=== "Using __init__ argument"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    class MyClient(BaseClient):
        pass


    client = MyClient(base_url="https://api.example.com")
    ```

=== "Overriding constructor"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    class MyClient(BaseClient):
        def __init__(self, *args, **kwargs):
            kwargs["base_url"] = "https://api.example.com"
            super().__init__(*args, **kwargs)


    client = MyClient()
    ```

### `headers`

Need to add some custom headers? No worries, BaseClient has got you covered.

=== "Using class attribute"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    from myapp.settings import settings


    class MyClient(BaseClient):
        base_url = "https://api.example.com"
        headers = {"Authorization": f"Bearer {settings.EXAMPLE_API_TOKEN}"}


    client = MyClient()
    ```
    !!! tip
        Prefer this approach if you don't need to change the `header` at runtime.

=== "Using __init__ argument"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    from myapp.settings import settings


    class MyClient(BaseClient):
        pass


    client = MyClient(
        base_url="https://api.example.com",
        headers={"Authorization": f"Bearer {settings.EXAMPLE_API_TOKEN}"
    )
    ```

=== "Overriding constructor"
    ```{.python title="my_client.py"}
    from declarativex import BaseClient

    class MyClient(BaseClient):
        def __init__(self, *args, **kwargs):
            kwargs["base_url"] = "https://api.example.com"
            kwargs["headers"] = {"Authorization": "Bearer <token>"}
            super().__init__(*args, **kwargs)


    client = MyClient()
    ```

## Wrapping Up

So there you have it, the `BaseClient` in all its glory. It's the cornerstone of DeclarativeX, designed to make your
life easier and your code cleaner.

Feel like diving deeper? Check out the [Decorators](./Decorators.md) and [Parameters](./Parameters.md) sections next.