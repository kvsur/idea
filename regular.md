<h2 style="color: #f97541;">代码规范概要</h2>


1. ### 命名规则
    1. #### 项目命名
        项目命名一般采用小写形式，有多个单词的项目名需要使用下划线或者减号线分隔，不建议采用驼峰形式；
        ```js
        my_project_name/my-project-name
        ```
    2. #### 文件命名
        1. 不管是样式文件，脚本文件还是html文件，都是类似于项目名的命名规则；
        2. 在结合React或者Vue进行开发的时候，因为是基于组件的开发形式，对于组件的命名，一般推荐采用首字母大写且继而使用驼峰命名形式；
    3. #### 变量命名
        ......
    4. #### 目录命名
        ```js
        scripts, styles, images, data_models
        ```
2. ### HTML
    1. #### 属性值
        1. 属性值一般推荐使用小写，多词使用减号线或者下划线，使用时尽量统一

        ```html
            <img src="images/company_logo.png" alt="Company">
            <h1 class="hello-world">Hello, world!</h1>
        ```

        2. 属性值使用双引号包括
    2. #### 属性书写顺序
        * class
        * id
        * name
        * data-*
        * src, for, type, href, value, max-length, max, min, pattern
        * placeholder, title, alt
        * aria-*, role
        * required, readonly, disabled
        class是为高可复用组件设计的，所以应该放在第一位；尽量少的使用id；
        对于boolean属性值，存在的话表示为true，不存在则为false

        ```html
            <input type="text" disabled>
            <input type="checkbox" value="1" checked>
            <select>
                <option value="1" selected>1</option>
            </select>
        ```
    3. #### 多使用H5最新的语义化标签
        例如：
        >* \<section>
        >* \<nav>
        >* \<article>
        >* \<aside>
        >* \<header>
        >* \<main>

        更多新标签可参考[H5标签列表](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5/HTML5_element_list 'H5标签列表')
    
    4. #### 区分开行内元素及块级元素
        不建议使用行内元素包裹块级元素的做法，然后使用display进行更改
        ```html
        <!-- not good -->
        <style>
            .artcle {
                display: block;
            }
        </style>
        <span class="article">
            <p>这里是内容</p>
        </span>

        <!-- good -->
        <article>
            <p>这里是内容</p>
        </artcle>
        ```
3. ### CSS
    1. #### 缩进
        缩进建议采用tab缩进（4个空格）

        ```css
        element {
            position: absolute;
            top: 10px;
            left: 10px;
            border-radius: 10px;
            width: 50px;
            height: 50px;
        }
        ````
    2. #### 分号
        每个属性声明末尾都要使用分号；
    3. #### 空格
        以下几种情况不需要空格：
        * 属性名后
        * 多个规则的分隔符‘，’前
        * 属性末尾的'('和')'
        * 行末不需要有空格
        以下几种情况需要空格：
        * 属性值前
        * 选择器'>''+''~'前后
        * '{'的前面
        * !important '!'前面
        * @else 前后
        * 属性值中的','后
        * 注释 '/'后 和 '/'前

        ```scss
            /* not good */
            .element {
                color :red! important;
                background-color: rgba(0,0,0,.5);
            }

            /* good */
            .element {
                color: red !important;
                background-color: rgba(0, 0, 0, .5);
            }

            /* not good */
            .element ,
            .dialog{
                ...
            }

            /* good */
            .element,
            .dialog {

            }

            /* not good */
            .element>.dialog{
                ...
            }

            /* good */
            .element > .dialog{
                ...
            }

            /* not good */
            .element{
                ...
            }

            /* good */
            .element {
                ...
            }

            /* not good */
            @if{
                ...
            }@else{
                ...
            }

            /* good */
            @if {
                ...
            } @else {
                ...
            }
        ```
    4. #### 换行
        * '{' 前不需要换行
        <br/>
        #### 以下需要换行：
        * '{'后 和 '}'前
        * 每个属性独占一行
        * 多个规则的分隔符','后

        ```css
        /* not good */
        .element
        {color: red; background-color: black;}

        /* good */
        .element {
            color: red;
            background-color: black;
        }

        /* not good */
        .element, .dialog {
            ...
        }

        /* good */
        .element,
        .dialog {
            ...
        }
        ```
    5. #### 注释与注释的缩进
        注释建议采用 /** comment */ 形式（即使在scss或者less中也不要使用 // comment）

        ```css
            /* Modal header */
        .modal-header {
            ...
        }

        /*
        * Modal header
        */
        .modal-header {
            ...
        }

        .modal-header {
            /* 50px */
            width: 50px;

            color: red; /* color red */
        }
        ```

    6. #### css中的命名规则及全局变量
        *在预编译css中，如果某些属性值在频繁出现使用，建议在全局或局部文件添加可复用的变量*
        * 类名采用小写字母，以中划线分隔
        * ID采用驼峰形式
        * 预编译css中的变量、函数、混合、placeholder采用驼峰命名

        ```scss
            /* class */
            .element-content {
                ...
            }

            /* id */
            #myDialog {
                ...
            }

            /* 变量 */
            $colorBlack: #000;

            /* 函数 */
            @function pxToRem($px) {
                ...
            }

            /* 混合 */
            @mixin centerBlock {
                ...
            }

            /* placeholder */
            %myDialog {
                ...
            }
        ```

    7. #### 属性简写
        属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；<br>
        > *其中 margin 和 padding 相反，需要使用简写*

        常见的属性简写包括：
        * font
        * background
        * transform
        * transition
        * animation

        ```css
            .box {
                /** 顺序是 上 右 下 左 */
                margin: 1px 1px 1px 1px;
                /** 顺序是 10px 指定上下， 20px 制定左右 */
                padding: 10px 12px;
            }
            .element {
                transition-delay: 2s;
                transition-timing-function: linear;
                transition-duration: 1s;
                transition-property: opacity;
            }
        ```
    8. #### 颜色
        颜色推荐使用十六进制的小写字母，能简写的减量简写；
        ```css
            /* not good */
            .element {
                color: #ABCDEF;
                background-color: #001122;
            }

            /* good */
            .element {
                color: #abcdef;
                background-color: #012;
            }
        ```
    9. #### 属性书写顺序
        属性声明可以做一个分组处理，组之间可以用行分开；
        推荐属性顺序可参照[属性声明顺序](https://github.com/kvsur/idea/blob/master/sort_attr.md)
        
        ```css
            .declaration-order {
                display: block;
                float: right;

                position: absolute;
                top: 0;
                right: 0;
                bottom: 0;
                left: 0;
                z-index: 100;

                border: 1px solid #e5e5e5;
                border-radius: 3px;
                width: 100px;
                height: 100px;

                font: normal 13px "Helvetica Neue", sans-serif;
                line-height: 1.5;
                text-align: center;

                color: #333;
                background-color: #f5f5f5;

                opacity: 1;
            }
        ```
    10. #### 兼容性书写规范
        1. 浏览器引擎前缀(Vendor Prefix)有哪些？ 
        >* -moz- /* 火狐等使用Mozilla浏览器引擎的浏览器 */ 
        >* -webkit- /* Safari, 谷歌浏览器等使用Webkit引擎的浏览器 */ 
        >* -o- /* Opera浏览器(早期) */ 
        >* -ms- /* Internet Explorer (不一定) */ 

        2. 使用浏览器引擎前缀的原因：
        >* 试验一些还未成为标准的的CSS属性——也许永远不会成为标准 
        >* 对新出现的标准的CSS3属性特征做实验性的实现 
        >* 对CSS3中一些新属性做等效语义的个性实现 

        3. 前缀使用规则是把不带前缀的版本放在最后一行：
        ```css
        -moz-border-radius: 10px; 
        -webkit-border-radius: 10px; 
        -o-border-radius: 10px; 
        border-radius: 10px; 
        ```

        4. 主要的需要添加浏览器引擎前缀(vendor-prefix)的属性包括：
        ```txt
        @keyframes
        移动和变换属性(transition-property, transition-duration, transition-timing-function, transition-delay)
        动画属性 (animation-name, animation-duration, animation-timing-function, animation-delay)
        border-radius
        box-shadow
        backface-visibility
        column属性
        flex属性
        perspective属性
        ```

        5. 复杂属性的一般写法（以keyframes为例）
        ```css
        @-webkit-keyframes fadeIn {
            0% { opacity: 0; } 100% { opacity: 0; }
        }
        @-moz-keyframes fadeIn {
            0% { opacity: 0; } 100% { opacity: 0; }
        }
        @-o-keyframes fadeIn {
            0% { opacity: 0; } 100% { opacity: 0; }
        }
        @-ms-keyframes fadeIn {
            0% { opacity: 0; } 100% { opacity: 0; }
        }
        ```
    11. #### 其他
        >* 不允许有空的规则；
        >* 元素选择器用小写字母；
        >* 去掉小数点前面的0；
        >* 去掉数字中不必要的小数点和末尾的0；
        >* 属性值'0'后面不要加单位；
        >* 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；
        >* 无前缀的标准属性应该写在有前缀的属性后面；
        >* 不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；
        >* 不要在一个文件里出现两个相同的规则；
        >* 用 border: 0; 代替 border: none;；
        >* 选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；
        >* 发布的代码中不要有 @import；
        >* 尽量少用'*'选择器。

4. ### JavaScript
    1. #### 缩进
        使用tab（4个空格）
        ```js
        var x = 1,
            y = 1;

        if (x < y) {
            x += 10;
        } else {
            x += 1;
        }
        ```
    2. #### 单行长度
        建议单行长度不要唱过80字符
    3. #### 分号
        以下几种情况后面强烈建议使用分号：
        * 变量声明
        * 表达式
        * import
        * return
        * throw
        * break
        * continue
        * do-while
    4. #### 空格
        以下情况需要使用空格:
        * 二元运算符前后
        * 三元运算符'?:'前后
        * 代码块'{'前
        * 下列关键字前：else, while, catch, finally
        * 下列关键字后：if, else, for, while, do, switch, case, try,catch, finally, with, return, typeof
        * 单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后
        * 对象的属性值前
        * for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
        * 无论是函数声明还是函数表达式，'{'前一定要有空格
        * 函数的参数之间

        ```javascript
            cosnt person = {
                name: 'lc',
                age: 23
            };

            /**
            * getInfo of a person
            */
            function getInfo(person = {}, context = {}) {
                const name = person.name ? person.name : 'lc',
                      age = person.age >= 0 ? person.age : 1;
                
                if (age < 20) {
                    age += 1;
                } else if (age > 40) {
                    age -= 10;
                }

                // output the key of person obj
                const keys = Object.keys(person);
                for (let key of keys) {
                    console.log(key);
                }
                
                try {
                    new Promise((resolve, reject) => {

                    });
                } catch (e) {

                }

                return `${name}: ${age} years old!!!`;
            }
        ```
    5. #### 空行
        * 变量声明后（当变量声明在代码块的最后一行时，则无需空行）
        * 注释前（当注释在代码块的第一行时，则无需空行）
        * 代码块后（在函数调用、数组、对象中则无需空行）
        * 文件最后保留一个空行
    6. #### 换行
        以下几种情况不需要换行：
        * 下列关键字后：else, catch, finally
        * 代码块'{'前

        以下几种情况需要换行：
        * 代码块'{'后和'}'前
        * 变量赋值后
    7. #### 单行注释及多行注释及函数注释
        单行注释/需要空行，具体注释之前需要空格，最后的/之前需要空格
        ```javascript

        /** this is comment */

        // this is comment

        /**
        * @author licheng
        * @param { string } c 这是一个参数
        */
        function foo(c) {
            return c**c;
        }
        ```
    8. #### 引号
        <div style="color: #f97541; font-size: 20px;">在js中能使用单引号的地方尽量使用单引号</div>
    9. #### 变量声明
    10. #### 函数

5. ### vue组件编码规范
    [vue组件编码规范](https://github.com/pablohpsilva/vuejs-component-style-guide/blob/master/README-CN.md#%E7%9B%AE%E5%BD%95 'vue组件编码规范')
6. ### 版本管理
    1. #### 分支开发
    2. #### 开发完成后需要先在本地测试，尝试部署、打包流程
    3. #### 无论何时提交代码前都需要优先pull远程分支上的代码进行update
    4. #### commit需要附带message
    5. #### 冲突解决优先保证远程端代码的正常（一般冲突都是未先pull就进行了commit操作）