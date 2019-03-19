Apollo ~ Next - Setup & Deploy

Project Setup
=============

```jsx
$ mkdir my_next_now_app
$ cd my_next_now_app
$ npm init -y
```

install dependecies

```jsx
$ npm i apollo-boost babel-plugin-styled-components graphql next next-with-apollo react react-apollo react-dom styled-components styled-normalize
```

update —\> package.json

```jsx
"scripts": {
    "dev": "next",
  }
```

AND this babel stuff in the package object

```jsx
 "//": "This is our babel config, I prefer this over a .babelrc file",
  "babel": {
    "env": {
      "development": {
        "presets": [
          "next/babel"
        ],
        "plugins": [
          [
            "styled-components",
            {
              "ssr": true,
              "displayName": true
            }
          ]
        ]
      },
      "production": {
        "presets": [
          "next/babel"
        ],
        "plugins": [
          [
            "styled-components",
            {
              "ssr": true,
              "displayName": true
            }
          ]
        ]
      },
      "test": {
        "presets": [
          [
            "next/babel",
            {
              "preset-env": {
                "modules": "commonjs"
              }
            }
          ]
        ],
        "plugins": [
          [
            "styled-components",
            {
              "ssr": true,
              "displayName": true
            }
          ]
        ]
      }
    }
  }
```

create —\> pages/index.js

```jsx
const Index = () => (
  <div>
    <p>Hello Next.js</p>
  </div>
)

export default Index
```

Run it

```jsx
$ npm run dev
```

Deploy to Now
=============

lets get this up and running on now first 

Do you already have the CLI installed!!

<https://zeit.co/docs/v2/getting-started/installation/>

Create —\> next.config.js

```jsx
module.exports = {
  target: 'serverless'
}
```

Create —\> now.json

<https://zeit.co/docs/v2/deployments/configuration/>

```jsx
{
  "version": 2,
  "name": "my_next_now_app",
  "builds": [{ "src": "next.config.js", "use": "@now/next" }]
}
```

Create —\> .nowignore

```jsx
node_modules
.vscode
.next
```

Update —\> .package.json

```jsx
{
  ...
  "scripts": {
    "dev": "next",
    "now-build": "next build"
  },
  ...
}
```

Deploy it

```jsx
$ now
```

As this is your first deploy you will get the alias address looks like

```jsx
Ready! Aliased to https://my_next_now_app.yourAccountName.now.sh [in clipboard] [46s]
```

All your subsequent deploys will alias to this, but will also get a unique url