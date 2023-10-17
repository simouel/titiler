# Module titiler.mosaic.factory

TiTiler.mosaic Router factories.

## Variables

```python3
MAX_THREADS
```

```python3
WGS84_CRS
```

```python3
img_endpoint_params
```

## Functions

    
### PixelSelectionParams

```python3
def PixelSelectionParams(
    pixel_selection: typing_extensions.Annotated[Literal['first', 'highest', 'lowest', 'mean', 'median', 'stdev', 'lastbandlow', 'lastbandhight'], Query(PydanticUndefined)] = 'first'
) -> rio_tiler.mosaic.methods.base.MosaicMethodBase
```

Returns the mosaic method used to combine datasets together.

## Classes

### MosaicTilerFactory

```python3
class MosaicTilerFactory(
    reader: Type[cogeo_mosaic.backends.base.BaseBackend] = <function MosaicBackend at 0x7f097eba3790>,
    router: fastapi.routing.APIRouter = <factory>,
    path_dependency: Callable[..., Any] = <function DatasetPathParams at 0x7f097e0a4e50>,
    dataset_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DatasetParams'>,
    layer_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.BidxExprParams'>,
    render_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.ImageRenderingParams'>,
    colormap_dependency: Callable[..., Union[Dict[int, Tuple[int, int, int, int]], Sequence[Tuple[Tuple[Union[float, int], Union[float, int]], Tuple[int, int, int, int]]], NoneType]] = <function create_colormap_dependency.<locals>.deps at 0x7f097e0a4dc0>,
    color_formula_dependency: Callable[..., Union[str, NoneType]] = <function ColorFormulaParams at 0x7f097dfb7f70>,
    rescale_dependency: Callable[..., Union[List[Tuple[float, ...]], NoneType]] = <function RescalingParams at 0x7f097e0a4ee0>,
    process_dependency: Callable[..., Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]] = <function Algorithms.dependency.<locals>.post_process at 0x7f097de3dee0>,
    reader_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    environment_dependency: Callable[..., Dict] = <function BaseTilerFactory.<lambda> at 0x7f097de3de50>,
    supported_tms: morecantile.defaults.TileMatrixSets = TileMatrixSets(tms={'CDB1GlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CDB1GlobalGrid.json'), 'CanadianNAD83_LCC': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/CanadianNAD83_LCC.json'), 'EuropeanETRS89_LAEAQuad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/EuropeanETRS89_LAEAQuad.json'), 'GNOSISGlobalGrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/GNOSISGlobalGrid.json'), 'LINZAntarticaMapTilegrid': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/LINZAntarticaMapTilegrid.json'), 'NZTM2000Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/NZTM2000Quad.json'), 'UPSAntarcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSAntarcticWGS84Quad.json'), 'UPSArcticWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UPSArcticWGS84Quad.json'), 'UTM31WGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/UTM31WGS84Quad.json'), 'WGS1984Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WGS1984Quad.json'), 'WebMercatorQuad': <TileMatrixSet title='Google Maps Compatible for the World' id='WebMercatorQuad' crs='http://www.opengis.net/def/crs/EPSG/0/3857>, 'WorldCRS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldCRS84Quad.json'), 'WorldMercatorWGS84Quad': PosixPath('/opt/hostedtoolcache/Python/3.8.18/x64/lib/python3.8/site-packages/morecantile/data/WorldMercatorWGS84Quad.json')}),
    default_tms: str = 'WebMercatorQuad',
    router_prefix: str = '',
    optional_headers: List[titiler.core.resources.enums.OptionalHeader] = <factory>,
    route_dependencies: List[Tuple[List[titiler.core.routing.EndpointScope], List[fastapi.params.Depends]]] = <factory>,
    extensions: List[titiler.core.factory.FactoryExtension] = <factory>,
    templates: starlette.templating.Jinja2Templates = <starlette.templating.Jinja2Templates object at 0x7f097dfc6d60>,
    dataset_reader: Union[Type[rio_tiler.io.base.BaseReader], Type[rio_tiler.io.base.MultiBaseReader], Type[rio_tiler.io.base.MultiBandReader]] = <class 'rio_tiler.io.rasterio.Reader'>,
    backend_dependency: Type[titiler.core.dependencies.DefaultDependency] = <class 'titiler.core.dependencies.DefaultDependency'>,
    pixel_selection_dependency: Callable[..., rio_tiler.mosaic.methods.base.MosaicMethodBase] = <function PixelSelectionParams at 0x7f097eba35e0>,
    add_viewer: bool = True
)
```

MosaicTiler Factory.

The main difference with titiler.endpoint.factory.TilerFactory is that this factory
needs the `reader` to be of `cogeo_mosaic.backends.BaseBackend` type (e.g MosaicBackend) and a `dataset_reader` (BaseReader).

#### Ancestors (in MRO)

* titiler.core.factory.BaseTilerFactory

#### Class variables

```python3
add_viewer
```

```python3
backend_dependency
```

```python3
dataset_dependency
```

```python3
dataset_reader
```

```python3
default_tms
```

```python3
layer_dependency
```

```python3
reader_dependency
```

```python3
render_dependency
```

```python3
router_prefix
```

```python3
supported_tms
```

```python3
templates
```

#### Methods

    
#### add_route_dependencies

```python3
def add_route_dependencies(
    self,
    *,
    scopes: List[titiler.core.routing.EndpointScope],
    dependencies=typing.List[fastapi.params.Depends]
)
```

Add dependencies to routes.

Allows a developer to add dependencies to a route after the route has been defined.

    
#### assets

```python3
def assets(
    self
)
```

Register /assets endpoint.

    
#### bounds

```python3
def bounds(
    self
)
```

Register /bounds endpoint.

    
#### color_formula_dependency

```python3
def color_formula_dependency(
    color_formula: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[str, NoneType]
```

ColorFormula Parameter.

    
#### colormap_dependency

```python3
def colormap_dependency(
    colormap_name: typing_extensions.Annotated[Literal['ice', 'rainbow', 'afmhot_r', 'brbg_r', 'gist_stern_r', 'rdylbu_r', 'algae_r', 'purd_r', 'balance', 'piyg', 'greys', 'gist_gray_r', 'hot_r', 'pubu_r', 'gnuplot2_r', 'rain', 'spectral_r', 'turbo_r', 'gist_rainbow_r', 'accent_r', 'coolwarm_r', 'gist_heat_r', 'summer', 'matter_r', 'prism', 'rdbu_r', 'haline', 'gnbu', 'terrain', 'winter', 'autumn_r', 'rdylbu', 'diff', 'gist_yarg_r', 'spring', 'turbid_r', 'winter_r', 'bugn', 'tab20c_r', 'copper_r', 'gnuplot_r', 'gist_stern', 'spring_r', 'prgn_r', 'spectral', 'wistia_r', 'orrd', 'topo', 'accent', 'magma_r', 'cmrmap', 'paired_r', 'twilight_shifted_r', 'diff_r', 'greys_r', 'delta', 'seismic', 'gist_ncar_r', 'blues_r', 'thermal', 'topo_r', 'puor_r', 'deep', 'pubu', 'nipy_spectral', 'cfastie', 'ocean_r', 'gist_earth_r', 'purples', 'delta_r', 'bone', 'gist_yarg', 'amp_r', 'plasma_r', 'tarn', 'pubugn_r', 'gnuplot', 'ice_r', 'gist_ncar', 'pastel1_r', 'oxy', 'ylgnbu', 'flag', 'dark2', 'cubehelix', 'turbid', 'jet', 'rdpu', 'oranges_r', 'bwr_r', 'tab10', 'bugn_r', 'tempo', 'tab10_r', 'bone_r', 'paired', 'brg', 'autumn', 'rdgy', 'rain_r', 'nipy_spectral_r', 'tab20', 'wistia', 'pink', 'twilight', 'hsv', 'magma', 'gray', 'curl_r', 'pink_r', 'phase', 'deep_r', 'gist_earth', 'cividis_r', 'oranges', 'curl', 'rainbow_r', 'copper', 'brg_r', 'ylorbr', 'ylorrd', 'rplumbo', 'viridis', 'greens', 'tempo_r', 'algae', 'thermal_r', 'pastel2_r', 'gist_gray', 'set2', 'inferno_r', 'solar', 'cool_r', 'pastel2', 'tab20b', 'binary', 'bwr', 'rdylgn_r', 'hsv_r', 'coolwarm', 'set2_r', 'gnuplot2', 'rdgy_r', 'ylgnbu_r', 'tab20_r', 'terrain_r', 'purples_r', 'cool', 'cubehelix_r', 'binary_r', 'jet_r', 'reds_r', 'greens_r', 'purd', 'flag_r', 'puor', 'prgn', 'dense', 'plasma', 'speed_r', 'cividis', 'bupu_r', 'dark2_r', 'inferno', 'set1_r', 'twilight_shifted', 'ylgn_r', 'bupu', 'gray_r', 'ylgn', 'rdbu', 'ylorrd_r', 'gist_heat', 'orrd_r', 'amp', 'balance_r', 'tarn_r', 'brbg', 'matter', 'set3', 'phase_r', 'pastel1', 'cmrmap_r', 'ocean', 'viridis_r', 'gnbu_r', 'hot', 'oxy_r', 'twilight_r', 'blues', 'haline_r', 'set3_r', 'pubugn', 'set1', 'tab20c', 'rdylgn', 'piyg_r', 'schwarzwald', 'ylorbr_r', 'speed', 'rdpu_r', 'turbo', 'summer_r', 'prism_r', 'dense_r', 'tab20b_r', 'gist_rainbow', 'afmhot', 'solar_r', 'seismic_r', 'reds'], Query(PydanticUndefined)] = None,
    colormap: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
)
```

    
#### environment_dependency

```python3
def environment_dependency(
    
)
```

    
#### info

```python3
def info(
    self
)
```

Register /info endpoint

    
#### map_viewer

```python3
def map_viewer(
    self
)
```

Register /map endpoint.

    
#### path_dependency

```python3
def path_dependency(
    url: typing_extensions.Annotated[str, Query(PydanticUndefined)]
) -> str
```

Create dataset path from args

    
#### pixel_selection_dependency

```python3
def pixel_selection_dependency(
    pixel_selection: typing_extensions.Annotated[Literal['first', 'highest', 'lowest', 'mean', 'median', 'stdev', 'lastbandlow', 'lastbandhight'], Query(PydanticUndefined)] = 'first'
) -> rio_tiler.mosaic.methods.base.MosaicMethodBase
```

Returns the mosaic method used to combine datasets together.

    
#### point

```python3
def point(
    self
)
```

Register /point endpoint.

    
#### process_dependency

```python3
def process_dependency(
    algorithm: typing_extensions.Annotated[Literal['hillshade', 'contours', 'normalizedIndex', 'terrarium', 'terrainrgb'], Query(PydanticUndefined)] = None,
    algorithm_params: typing_extensions.Annotated[Union[str, NoneType], Query(PydanticUndefined)] = None
) -> Union[titiler.core.algorithm.base.BaseAlgorithm, NoneType]
```

Data Post-Processing options.

    
#### read

```python3
def read(
    self
)
```

Register / (Get) Read endpoint.

    
#### reader

```python3
def reader(
    input: str,
    *args: Any,
    **kwargs: Any
) -> cogeo_mosaic.backends.base.BaseBackend
```

Select mosaic backend for input.

    
#### register_routes

```python3
def register_routes(
    self
)
```

This Method register routes to the router.

Because we wrap the endpoints in a class we cannot define the routes as
methods (because of the self argument). The HACK is to define routes inside
the class method and register them after the class initialization.

    
#### rescale_dependency

```python3
def rescale_dependency(
    rescale: typing_extensions.Annotated[Union[List[str], NoneType], Query(PydanticUndefined)] = None
) -> Union[List[Tuple[float, ...]], NoneType]
```

Min/Max data Rescaling

    
#### tile

```python3
def tile(
    self
)
```

Register /tiles endpoints.

    
#### tilejson

```python3
def tilejson(
    self
)
```

Add tilejson endpoint.

    
#### url_for

```python3
def url_for(
    self,
    request: starlette.requests.Request,
    name: str,
    **path_params: Any
) -> str
```

Return full url (with prefix) for a specific endpoint.

    
#### validate

```python3
def validate(
    self
)
```

Register /validate endpoint.

    
#### wmts

```python3
def wmts(
    self
)
```

Add wmts endpoint.