# HTTP协议
### 请求方式
#### 知识
1、GET：从服务器获取指定资源。它用于请求服务器发送某个资源的内容，并将其作为响应返回给客户端。
2、POST：向服务器提交数据，用于创建新的资源。通常用于向服务器发送表单数据或在服务器上执行一些操作。
3、PUT：向服务器上传或替换指定资源。它用于将请求中的实体存储在服务器上，如果资源已存在，则替换它。
4、DELETE：删除服务器上的指定资源。它用于请求服务器删除指定的资源。
5、HEAD：与GET方法类似，但只请求获取资源的头部信息，而不返回实际内容。它用于获取资源的元数据，例如最后修改时间或内容长等。
6、OPTIONS：获取服务器支持的通信选项。它用于请求服务器返回当前资源所支持的HTTP方法。
7、TRACE：用于执行一个远程回环测试。服务器将接收到的请求返回给客户端，用于测试或诊断。
8、CONNECT：用于代理服务器，将连接转换为透明的TCP/IP通道。它允许客户端与服务器之间建立隧道，用于加密和其他目的。
#### 代码实现
```python
import requests
# response = requests.request('方法名','URL地址')
response = requests.request('get','https://example.com')
print(response.text)
```
```shell
# curl -X 方法名 URL地址
curl -X GET https://example.com
```
### 302跳转
#### 知识
HTTP协议中的临时重定向是指HTTP响应状态码302。当客户端向服务器发送一个请求，服务器无法直接提供请求资源，但可以提供一个临时重定向地址，让客户端重新发送请求到新的地址，以获取所需的资源。
#### 代码实现
```python
import requests
# response = requests.request('方法名','URL地址',禁用重定向)
response = requests.request('get','https://example.com',allow_redirects=False)
print(response.text)
```
```shell
# curl URL地址
curl https://example.com
```
### Cookie
#### 知识
Cookie欺骗、认证和伪造是与Web安全相关的概念，涉及到操纵和利用Cookie来进行攻击或欺骗。

* Cookie欺骗（Cookie Spoofing）：Cookie欺骗是指攻击者通过操纵Cookie值来伪装成合法用户或以其他方式欺骗系统。攻击者可以修改Cookie中的数据，例如篡改用户身份标识或修改会话状态，从而获得未经授权的访问权限。防范Cookie欺骗的方法包括使用安全的Cookie标志（Secure和HttpOnly），对Cookie进行加密或签名，以及实施其他安全措施来验证和保护Cookie的完整性。

* Cookie认证（Cookie Authentication）：Cookie认证是一种常见的身份验证机制，用于跟踪和管理用户会话状态。在Cookie认证中，服务器通过在响应中设置一个包含用户标识信息的Cookie，然后在后续的请求中验证该Cookie来识别和验证用户。对于安全的Cookie认证，建议使用安全标志（Secure）以确保Cookie仅通过加密的安全连接发送，并使用HttpOnly标志以防止客户端脚本访问Cookie。

* Cookie伪造（Cookie Forgery）：Cookie伪造是指攻击者通过伪造或生成合法的Cookie值来冒充用户身份或以其他方式进行欺骗。攻击者可以利用弱密码哈希算法、会话劫持等漏洞，生成或篡改Cookie值以获取非法访问权限。防范Cookie伪造的方法包括使用强大的加密和哈希算法生成Cookie值，使用安全的会话管理技术（如使用随机的会话标识符）以减少伪造的风险，并进行适当的身份验证和授权控制。
#### 代码实现
```python
import requests
cookies = {
    'key':'value'
}
# response = requests.request('方法名','URL地址',携带cookie)
response = requests.request('get','https://example.com',cookies=cookies)
print(response.text)
```
```shell
# curl -b cookie信息 URL地址
curl -b "key=value" https://example.com
```
### 基础认证
#### 知识
在HTTP中，基本认证（英语：Basic access authentication）是允许http用户代理（如：网页浏览器）在请求时，提供 用户名 和 密码 的一种方式。
#### 代码实现
```python
import requests
username = 'username'
password = 'password'
response = requests.request('get','https://example.com',auth=(username,password))
print(response.text)
```
```shell
curl -u "username:password" https://example.com
```
### 响应包源代码
#### 知识
浏览器右键即可查看源代码
#### 代码实现
```python
import requests
# response = requests.request('方法名','URL地址')
response = requests.request('get','https://example.com')
print(response.text)
```
```shell
curl -X GET https://example.com
```