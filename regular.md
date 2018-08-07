## 代码规范概要
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
        * 多个贵族的分隔符‘，’前
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

5. ### vue组件编码规范
    [vue组件编码规范](https://github.com/pablohpsilva/vuejs-component-style-guide/blob/master/README-CN.md#%E7%9B%AE%E5%BD%95 'vue组件编码规范')
6. ### 版本管理