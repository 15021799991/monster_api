# 入门指引  

## 申请API权限

测试版本需人工申请appId/appSecret。

**_注意： 请勿向任何人泄露这两个参数，这两个参数关乎您账号的安全。_**    
     
## 参数签名    

用户提交的参数除appSign外，都要参与签名。    

首先，将待签名字符串要求按照参数名进行排序(首先比较所有参数名的第一个字母，按abcd顺序排列，若遇到相同首字母，则看第二个字母，以此类推)。   

例如：对于如下的参数进行签名   

	string[] parameters={"symbol=MR/ETH","appId=mst236153ce620f3fbc",timestamp=1537238490607"，nonceStr=4800e5f4...."};     

生成待签名的字符串    

	appId=mst236153ce620f3fbc&nonceStr=4800e5f4....&symbol=MR/ETH&timestamp=1537238490607

然后，将待签名字符串添加私钥参数生成最终待签名字符串。例如：

	appId=mst236153ce620f3fbc&nonceStr=4800e5f4....&symbol=MR/ETH&timestamp=1537238490607&key=appSecret

注意，`&nonceStr=4800e5f4...`32位随机字符串为必传参数, `&key=appSecret` 为签名必传参数, `&timestamp=1537238490607`时间戳为必传参数。   

最后，是利用32位MD5算法，对最终待签名字符串进行签名运算，从而得到签名结果字符串(该字符串赋值于参数sign)，MD5计算结果中字母全部大写。  

## 联系我们
官方邮箱: support@monster.one
