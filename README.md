Core
=========

The **Core** object provides access to methods that are available for use by Bridge layers that connect the Constellation Core to a UI Library implementation.


Table of contents
=================

<!--ts-->
   * [Redux](#redux)
   * [Error handling](#error-handling)
   * [Validations](#installation)
   * [Expression](#expression)
   * [Server whens](#server-whens)
   * [Semantic url handling](#semantic-url-handling)
   * [Action processing](#action-processing)
   * [Metadata iterator](#metadata-iterator)
   * [Asset loader](#asset-loader)
<!--te-->



### Redux




### Error handling





### Validations





### Expression









### Asset loader

Exposes APIs to load the script files and css files as of now.

AssetLoader class exposes following methods : 

-  register 
- getLoader
- getStaticServerUrl 
- initServer
- loadAssets

By default, out in-built loader for js/css will be used.
Custom loaders can be registered using viz. 'Font-loader'
```bash
➥ PCore.getAssetLoader().register('font-loader',fontLoaderFn);
```

Custom loaders can be used in this way. Assets need to passed asset type and url.

```bash
➥ PCore.getAssetLoader().getLoader('font-loader')('web-font','https://fonts.googleapis.com/css2?family=Noto+Sans&display=swap');
```

getStaticServerUrl Method is used to fetch static content url :

```bash
➥ PCore.getAssetLoader().getStaticServerUrl();
```

initServer Method is sets the static content url :

```bash
➥ PCore.getAssetLoader().initServer('http://localhost:1080/prweb/AppName/');
```
