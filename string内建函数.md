# string内建函数
* >string.capitalize()  
将字符串的第一个字符大写
* >string.count(str,beg=0,end=len(string))  
返回str在string里出现的次数，如果beg或者end指定范围，则返回指定范围内str出现的次数
* >string.endswith(str,beg=0,end=len(string))  
检查string是否以str结束，如果是，则返回True，否则返回False，可指定范围beg和end
* > string.find(str,beg=0,end=len(string))  
检查str是否包含在字符串string中，如果包含则返回第一个匹配到的索引值，不包含则返回-1，可指定范围beg和end
* >string.index(str,beg=0,end=len(string))  
检查str是否包含在字符串string中，如果包含则返回第一个匹配到的索引值，不包含则返回异常，可指定范围beg和end
* >string.isalnum()  
如果字符串的字符个数>=1且所有字符都是字母或者数字，则返回True，否则返回False
* >string.isalpha()  
如果字符串的字符个数>=1且所有字符都是字母,则返回True，否则返回False
* >string.isdigit()  
如果字符串的字符个数>=1且所有字符都是数字，则返回True，否则返回False