```python
from flask import Flask
def create_app():
    app = Flask(__name__)
    app.config			# from_mapping/from_pyfile
    @app.route('/')
    def index():
        return 'Hello World'
    return app
```

```python
eval()
exec()
```

