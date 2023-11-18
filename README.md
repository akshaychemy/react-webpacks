# React + Vite

1.Install webpack and other necessary packages using npm.

bash
Copy code
``````
npm install --save-dev webpack webpack-cli webpack-dev-server

``````


Install Babel and related packages:
Install Babel and its related packages to transpile JSX and ES6 code.

``````
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
``````

3.Create a Babel configuration file named .babelrc in the project root:

``````
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}

``````

Create a webpack configuration file:
Create a webpack.config.js file in the root of your project. This file will define how webpack should bundle your application.
``````
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: 'babel-loader',
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  resolve: {
    extensions: ['.js', '.jsx'],
  },
  devServer: {
    contentBase: './dist',
    port: 3000,
    hot: true,
  },
};
``````


update package

```
"scripts": {
  "start": "webpack serve --mode development --open",
  "build": "webpack --mode production"
}
```