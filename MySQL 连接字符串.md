jdbc:mysql://127.0.0.1:3306/******?characterEncoding=utf8&useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
解析：
    characterEncoding=utf8  （字符编码）
    useSSL=false    （发现是8版本开始才需要添加，5.X印象中不需要，添加这个参数可能和MySQL的SSL连接设置有关系）
    serverTimezone=UTC  （当连接数据库时候，出现Time Zone错误时添加此参数，我貌似是使用Druid连接池时才出现的这个问题）
    allowPublicKeyRetrieval=true    （使用root账户登陆没问题，使用普通账户会提示Public Key Retrieval错误）