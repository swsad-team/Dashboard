# 本地安装部署说明

## 环境需求
* NodeJS 10+

## 前端
clone 项目
```shell
git clone https://github.com/swsad-team/FrontEnd.git
cd FrontEnd
```
安装依赖

```shell
npm install
```
配置环境变量
```shell
echo "REACT_APP_API_URL=[YOUR API URL]" >>. env 
```
 构建静态文件
```shell
npm run build
```
启动静态文件服务器
```shell
npx serve -s build
```

## 后端

clone 项目
```shell
git clone https://github.com/swsad-team/BackEnd.git
cd BackEnd
```
安装依赖
```shell
npm install
```

配置环境变量
```shell
echo "JWT_KEY=[YOUR JWT KEY]" >>. env 
echo "MONGO_DB_URL=[YOUR MONGODB URL]" >>. env 
```
编译并启动 API 服务器
```shell
npm run compile
npm start
```
