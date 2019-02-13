get_json
================

- **get_json(force=False, silent=False, cache=True)**

Parse and return the data as JSON. If the mimetype does not indicate JSON (application/json, see is_json()), this returns None unless force is true. If parsing fails, on_json_loading_failed() is called and its return value is used as the return value.

~~~python
request.get_json(True, True, True)
~~~

> Parameters:
> - `force` – Ignore the mimetype and always try to parse JSON.
> - `silent` – Silence parsing errors and return None instead.
> - `cache` – Store the parsed JSON to return for subsequent calls.

*reference:* `http://flask.pocoo.org/docs/1.0/api/#flask.Request.get_json`