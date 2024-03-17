## 基于Dokcer安装部署Running Page
本项目基于 [running_page](https://github.com/yihong0618/running_page/blob/master/README-CN.md) , 更改了Dockerfile文件，新增了Keep基于Docker部署以及Docker run运行时更改构建时设置的容器参数。可参考原项目操作步骤

## Docker

```bash
# NRC
docker build -t running_page:latest . --build-arg app=NRC --build-arg nike_refresh_token=""

# Garmin
docker build -t running_page:latest . --build-arg app=Garmin --build-arg secret_string=""

# Garmin-CN
docker build -t running_page:latest . --build-arg app=Garmin-CN --build-arg secret_string=""

# Strava
docker build -t running_page:latest . --build-arg app=Strava --build-arg client_id=""  --build-arg client_secret=""  --build-arg refresh_token=""

#Nike_to_Strava
docker build -t running_page:latest . --build-arg app=Nike_to_Strava  --build-arg nike_refresh_token="" --build-arg client_id=""  --build-arg client_secret=""  --build-arg refresh_token=""

#Keep
docker build -t running_page:latest . --build-arg app=Keep --build-arg your_mobile=""  --build-arg your_password=""

#启动,所有参数默认不变，按照上方构建的镜像参数来
docker run -itd -p 80:80   running_page:latest

# NRC,下方nike_refresh_token更改为NRC的token
docker run -itd -p 80:80 -e E_app=NRC -e E_nike_refresh_token=nike_refresh_token running_page:latest

# Garmin，下方secret_string改为对应secret_string
docker run -itd -p 80:80 -e E_app=Garmin -e E_secret_string=secret_string running_page:latest

# Garmin-CN下方secret_string改为对应secret_string
docker run -itd -p 80:80 -e E_app=Garmin-CN -e E_secret_string=secret_string running_page:latest

# Strava，下方client_id改为登录的StravaID，client_secret改为Strava个人secret,refresh_token改为Strava个人token
docker run -itd -p 80:80 -e E_app=Strava -e E_client_id=client_id -e E_client_secret=client_secret -e E_refresh_token=refresh_token running_page:latest

#Nike_to_Strava，下方nike_refresh_token更改为NRC的token，client_id改为登录的StravaID，client_secret改为Strava个人secret，refresh_token改为Strava个人token
docker run -itd -p 80:80 -e E_app=Nike_to_Strava -e E_nike_refresh_token=nike_refresh_token -e E_client_id=client_id -e E_client_secret=client_secret -e E_refresh_token=refresh_token running_page:latest

#Keep,下方your_mobile改为登录手机号，your_password改为登录密码
docker run -itd -p 80:80 -e E_app=Keep -e E_your_mobile=your_mobile -e E_your_password=your_password running_page:latest

#访问
访问 ip:80 查看

```
