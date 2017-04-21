# apply-call

## 是什么玩意？
   apply()和call()方法是是为了改变某个函数运行时的 context 即上下文而存在的，换句话说，就是为了改变函数体内部 this 的指向。二者是一样的东西。【JavaScript 的函数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念。】
   
obj.call(thisObj, arg1, arg2, ...);
obj.apply(thisObj, [arg1, arg2, ...]);

两者作用一致，都是把obj(即this)绑定到thisObj，这时候thisObj具备了obj的属性和方法。或者说thisObj『继承』了obj的属性和方法。
唯一区别是apply接受的是数组参数，call接受的是连续参数。
## 怎么用
      function add(j, k){
          return j+k;
       }

    function sub(j, k){
        return j-k;
    }
    控制台输出
    add(5,3); //8
    add.call(sub, 5, 3); //8   sub具有了add的方法和属性
    add.apply(sub, [5, 3]); //8 sub具有了add的方法和属性

    sub(5, 3); //2
    sub.call(add, 5, 3); //2 add具有了sub的方法和属性
    sub.apply(add, [5, 3]); //2 add具有了sub的方法和属性

## 有啥好处
####  继承！！上demo
    var Parent = function(){
        this.name = "yjc";
        this.age = 22;
    }

    var child = {};

    console.log(child);//Object {} ,空对象

    Parent.call(child);

    console.log(child); //Object {name: "yjc", age: 22}
