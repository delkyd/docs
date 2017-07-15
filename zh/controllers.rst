控制器
######

.. php:namespace:: Cake\Controller

.. php:class:: Controller

控制论器即MVC模式中的'C'. 路由被应用后正确的控制器将被定位, 您的控制器中的动作将被调用.控制器应解析处理请求,确保正确的模型被调用,正确的输出或者视图被渲染.控制器可以理解为模型和视图的中间层.通常来说，应保证控制器尽可能简单，模型尽可能充分.这样能有助于提升代码的可重用度,也能让代码易于测试.

通常,一个控制器用于管理一个模型的业务逻辑.例如,你准备为一个在线面包店创建一个站点,您需要食谱控制器管理您的食谱，材料控制器管理您的材料.当然,您也可以让控制器管理一个以上模型. 在CakePHP中,控制器被命名为其处理的主模型名称之后.

应用程序的控制器扩展了 ``AppController`` 类,扩展了核心  :php:class:`Controller` 类. ``AppController`` 类被定义于 **src/Controller/AppController.php** 它包含了您应用中所有控制器之间公用的方法.

控制器提供了用于处理请求的方法. 它们被称作*actions*(动作).通常控制器中的每个公共方法是一个动作,它能被通过一个URL地址访问.每个动作均负责处理请求并创建响应输出. 通常响应是通过渲染视图的方式,但也允许通过其它方式创建响应.


.. _app-controller:

App 控制器
==================

如引文所述, ``AppController`` 类是应用程序中所有控制器的父类.  ``AppController`` 本身扩展了CakePHP中所包含的
:php:class:`Cake\\Controller\\Controller` 类 .
``AppController`` 定义于 **src/Controller/AppController.php** 内容如下::

    namespace App\Controller;

    use Cake\Controller\Controller;

    class AppController extends Controller
    {
    }

创建于``AppController``中的控制器属性和方法奖在所有您扩展自它的控制器中生效.
组件(您稍后将了解到的) 是在多个(但不是所有)控制器中使用通用代码的最好的方式.

您可以在 ``AppController`` 中装载用于应用中所有控制器的通用的组件. CakePHP 提供了一个 ``initialize()`` 方法 ,其调用于控制器的构造方法之后，主要用于以下场景::

    namespace App\Controller;

    use Cake\Controller\Controller;

    class AppController extends Controller
    {

        public function initialize()
        {
            // Always enable the CSRF component.
            $this->loadComponent('Csrf');
        }

    }

除 ``initialize()`` 方法外, 比较老的 ``$components`` 属性也支持用于定义缺省需要装载的组件. 根据面向对象的继承规则, 组件和辅助类在控制器中则被特别对待. 因此, ``AppController`` 的属性值应用于所有的子控制器类. 当然子类中的值通常也将覆盖 ``AppController``中的定义.

todo.....

.. note::
    The documentation is not currently supported in Chinese language for this
    page.

    Please feel free to send us a pull request on
    `Github <https://github.com/cakephp/docs>`_ or use the **Improve This Doc**
    button to directly propose your changes.

    You can refer to the English version in the select top menu to have
    information about this page's topic.

关于控制器的更多内容
====================

.. toctree::
    :maxdepth: 1

    controllers/pages-controller
    controllers/components

.. meta::
    :title lang=zh: Controllers
    :keywords lang=zh: correct models,controller class,controller controller,core library,single model,request data,middle man,bakery,mvc,attributes,logic,recipes
