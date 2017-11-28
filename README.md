# Regular-Expression
正则表达式

1.正则表达式test()，慎用g
今天在将这个表达式时，发现了一个问题：
test()检测指定字符串是否存在返回一个布尔值

 var  reg=/cat/g;
var str='this a cat,this a dog'; 
document.write(reg.test(s)); 
document.write(reg.test(str)); 
按道理两次打印出来都应该是true,true,而最终结果为true,false。
此时我们需要注意啦，在我们定义的正则表达式中后面加上了搜索的方式，g表示全文查找。而且在正则表达式内部有一个lastIndex来记录匹配的位置，第一次调用test()后，那么lastIndex就不再等于0，而是10，当下次在调用该方法的时候，字符串的匹配会从lastIndex位置进行匹配，故最终返回false.所以不要随意添加g.
遇到此种情况后的解决方法：
1.去除g;
2.在第二次使用前，设置reg.lastIndex=0即可。
