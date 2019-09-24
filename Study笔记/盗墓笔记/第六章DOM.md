#第六章  DOM
###6.1  DOM概述
6.1.1  DOM的概念
DOM文档对象模型，DOM对象不仅仅是一个普通的内置对象，他还是一个巨大的API的核心对象，它将文档的内容呈现在js面前，并赋予了js操作文档的能力

6.1.2  DOM和JavaScript的关系
一个web页面是一个文档，这文档可以在浏览器窗口或者作为html源代码显示出来，但上述两种情况都是同一个文档，DOM提供了对同一份文档的另一种表现，存储和操作的方式，DOM能够使用JavaScript脚本语言进行修改

6.1.3  DOM节点
加载html页面是，web浏览器生成一个属性结构，用来表示页面的内部结构，DOM将这种结构理解为节点组成，根据html DOM标准，html文档找到那个的所有内容都是节点
>整个文档是一个文档节点
>每个html元素是元素节点
>html元素内容的文本是文本节点
>每个html属性都是属性节点
>注释也是节点，叫注释节点

6.1.4  DOM树
DOM树体现着html页面的层级结构，而DOM树有DOM文档树和DOM元素树两种，DOM元素树包含的只有元素节点，而DOM文档树则包括DOM文档中的所有内容

###6.2  获取元素
6.2.1  用id获取元素
getElementById()的方法，接受一个参数：获取元素的id，如果找到相应元素，则返回该元素，否则返回null

       //用变量接住  在文档中   找  元素  用id  'd'
	   var d = document.getElementById('d');

6.2.2  用标签名获取元素
getElementsByTagName()可以获取该元素名称下所有的元素，返回一个伪数组，或者说是节点列表

      var lis = document.getElementsByTagName('li');
	  //伪数组
	  console.log(lis);

在某一个元素中，并不是太全局文档中利用标签获取元素，这样更加精准

     var ul = document.getElementById('ul');
	 var list = document.getElementsByTagName('li');
	 console.log(list);

当元素只有一个的时候，返回的也依然是一个列表，而不是一个元素，可以通过数组的下表找到该元素

     var div = document.getElementsByTagName('div');
	 console.log(div[0]);

6.2.3  用类名获取元素

     var a = document.getElementsByClassName('a');
	 console.log(a);

6.3.1  用css选择器获取元素

    querySelector();只能找到元素列表的第一个元素
    querySelectorAll();可以全部找到

#6.3  获取和设置元素中的其他信息
6.3.1  获取元素名
当我们使用id获取元素的时候，元素的名称会和整个元素一起显示出来，如果想要拿到该元素的元素名，也就是标签名则需要用tagName属性，该属性只能获取，不能设置

         var div=document.getElementById('my')
         console.log(div.tagName);//DIV

6.3.2  获取元素节点里的内容
当获取了元素之后，如果我们需要拿到元素中的内容，则需要用另一种方法得到。元素里的内容可能包括：文本或元素。需要用innerHTML属性
        var div = document.getElementById('mydiv');
        console.log(div.innerHTML);

innerHTML属性除了可以获取标签内的内容外，还可以设置标签内的内容。
        var div = document.getElementById('mydiv');
        console.log(div.innerHTML);

        div.innerHTML = '你好';

6.3.3  获取元素节点中的文本
利用innerText属性获取的只能是文本节点，不能是其他，当然innerText属性除了获取，也可以设置元素中的文本

        var div = document.getElementById('mydiv');
        console.log(div.innerText);

        div.innerText = '你好';

6.3.4  获取元素的类名
利用className属性获取元素的类名，以字符串的形式返回，同时可以设置新的class类名，需要注意的是，返回值是一个字符串
       var mydiv = document.getElementById('mydiv');
	   console.log(div.className);

如果更换其中一个类，则考虑该字符串中其他类是否一起设置
  
       div.className = 'd a c';
	   console.log(div.className);

6.3.5  获取元素样式
style属性可以获取元素内联样式的所有属性，当然如果继续在style中找属性名  如：backgroundcolor，就可以得到该属性的字符串的形式返回，同时也可以设置该属性，从而达到增加或更改样式，需要注意的是，以js形式增加的样式的优先级大于css优先级

      <div style="background-color: blue;"></div>
	  <script type="text/javascript">
	        var div = document.getElementsByTagName('div');
			console.log(div[0].style.backgroundColor);
	  </script>

6.3.6  获取元素属性
getAttribute('')可以获取元素的某个属性，要将属性名称放在括号中记得要用引号括起来，返回值就是字符串形式的属性值

      var div = document.getElementById('mydiv');
	  var a = document.getElementsByTagName('a');
			
	  console.log(div.getAttribute('id'));
	  console.log(a[0].getAttribute('href'));

6.3.7  设置元素属性
setAttribute()可以设置元素的某个属性，第一个参数是属性名，第二个参数是属性值，都需要引号括起来逗号分离

     var div = document.getElementsByTagName('div');
	 var a = document.getElementsByTagName('a');
			
	 div[0].setAttribute('id','mydiv');
	 a[0].setActive('href','http://www.baidu.com');

6.3.8  删除元素属性
使用removeAttribute（），可以删除某个元素的某个属性，括号中放入需要删除的属性名，用引号包裹

      var div = document.getElementById('mydiv');
	  div.removeAttribute('id');