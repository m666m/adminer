# adminer

Containerized running of dockette/adminer.

## docker run

独立运行 dg 版，精简够用的选择：

    $ docker run -d \
        --name adminer-dg \
        -p 8080:80 \
        --add-host=host.docker.internal:host-gateway \
        --network db-net \
        dockette/adminer:dg

如果要访问其他容器化数据库，需要 --network db-net。这样，在 Adminer 登录页面就可以直接用对方容器的服务名（如 mysql）作为“服务器”地址。访问宿主机或其他内网数据库：不需要指定。默认的桥接网络（bridge）模式下，只需配合上面的 host.docker.internal 来访问宿主机服务，或直接使用数据库服务器的真实内网IP（如 192.168.1.100）即可。
