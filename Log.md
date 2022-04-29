# .env.development 和 .env.production 文件中的变量，带有 GRIDSOME_ 服务端和客户端都能访问到，前面不带 GRIDSOME_ 的只能服务端能访问到

# 部署到 vercel ，需要 npm install 安装依赖时失败

![部署失败](41121651200945_.pic.jpg)

```javascript
{
  "name": "blog-with-gridsome",
  "private": true,
  "scripts": {
    "build": "gridsome build",
    "develop": "gridsome develop",
    "explore": "gridsome explore"
  },
  "dependencies": {
    "@fortawesome/fontawesome-free": "^5.14.0",
    "@gridsome/source-filesystem": "^0.6.2",
    "@gridsome/source-strapi": "^0.2.0",
    "@gridsome/transformer-remark": "^0.6.2",
    "axios": "^0.20.0",
    "bootstrap": "^4.5.2",
    "gridsome": "^0.7.0",
    "markdown-it": "^11.0.0"
  }
}
```

```javascript
{
  "name": "mygridsome-mac",
  "private": true,
  "scripts": {
    "develop": "gridsome develop",
    "explore": "gridsome explore",
    "build": "gridsome build"
  },
  "dependencies": {
    "@fortawesome/fontawesome-free": "^5.15.3",
    "@gridsome/source-filesystem": "^0.6.2",
    "@gridsome/source-strapi": "^0.2.0",
    "@gridsome/transformer-remark": "^0.6.4",
    "axios": "^0.21.1",
    "bootstrap": "^5.0.2",
    "gridsome": "^0.7.0",
    "markdown-it": "^12.1.0"
  }
}

```