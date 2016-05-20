# reapop-theme-wybo

[![npm version](https://img.shields.io/npm/v/reapop-theme-wybo.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-wybo) [![npm dependencies](https://img.shields.io/david/LouisBarranqueiro/reapop-theme-wybo.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-wybo) [![npm download/month](https://img.shields.io/npm/dm/reapop-theme-wybo.svg?style=flat-square)](https://www.npmjs.com/package/reapop-theme-wybo) [![gitter chat](https://img.shields.io/gitter/room/LouisBarranqueiro/reapop-theme-wybo.svg?style=flat-square)](https://gitter.im/LouisBarranqueiro/reapop-theme-wybo)

Official theme for [Reapop](https://github.com/LouisBarranqueiro/reapop) 

## Installation

```
npm install reapop-theme-wybo --save
```

## Integration

### Update webpack config

You have to define some loaders to handle files of theme. If it's not already the case, you need to install :

 - **style-loader** with `npm install style-loader --save-dev`
 - **css-loader** with `npm install css-loader --save-dev`
 - **sass-loader** with `npm install sass-loader --save-dev`
 - **url-loader** with `npm install url-loader --save-dev`
 - **file-loader** with `npm install file-loader --save-dev`

Look at this example, you can use it in for your project. Check out configuration of [Reapop Demo](https://github.com/LouisBarranqueiro/reapop.blob/master/demo/build/webpack.config.js) to see a complete example.

``` js
// CSS loader with some configuration
// read https://github.com/webpack/css-loader to understand each query parameters
var CSSLoader = [
  'css?sourceMap&-minimize',
  'modules',
  'importLoaders=1',
  'localIndentName=[name]__[local]__[hash:base64:5]'
].join('&');

module.exports = {
  module: {
    loaders: [{
      test: /\.scss$/,
      loaders: ['style', CSSLoader, 'sass']
    }, {
      test: /\.woff(2)?(\?v=[0-9]\.[0-9]\.[0-9])?$/,
      loader: "url-loader?limit=10000&minetype=application/font-woff"
    }, {
      test: /\.(ttf|eot|svg)(\?v=[0-9]\.[0-9]\.[0-9])?$/,
      loader: "file-loader"
    }]
  }
};
```

### Set the theme

``` js
import React, {Component} from 'react';
import NotificationsSystem from 'reapop';
// 1. import theme
import theme from 'reapop-theme-wybo';
// 
class ATopLevelComponent extends Component {
  render() { 
   // 2. set `theme` prop
    return (
      <div>
        <NotificationsSystem theme={theme}/>
      </div>
    );
  }
}
```

## License 

Reapop-theme-wybo is under [GPL-3.0 License](https://github.com/LouisBarranqueiro/reapop/blob/master/LICENSE)