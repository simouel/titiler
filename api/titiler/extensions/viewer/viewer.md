# Module titiler.extensions.viewer

titiler Viewer Extensions.

## Variables

```python3
DEFAULT_TEMPLATES
```

## Classes

### cogViewerExtension

```python3
class cogViewerExtension(
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7f161ac06160>
)
```

Add /viewer endpoint to the TilerFactory.

#### Ancestors (in MRO)

* titiler.core.factory.FactoryExtension

#### Class variables

```python3
templates
```

#### Methods

    
#### register

```python3
def register(
    self,
    factory: titiler.core.factory.BaseTilerFactory
)
```

Register endpoint to the tiler factory.

### stacViewerExtension

```python3
class stacViewerExtension(
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7f161ac06160>
)
```

Add /viewer endpoint to the TilerFactory.

#### Ancestors (in MRO)

* titiler.core.factory.FactoryExtension

#### Class variables

```python3
templates
```

#### Methods

    
#### register

```python3
def register(
    self,
    factory: titiler.core.factory.BaseTilerFactory
)
```

Register endpoint to the tiler factory.