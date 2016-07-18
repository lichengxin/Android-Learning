###**学习MVP**
> MVP把Activity中的UI逻辑抽象成View接口，把业务逻辑抽象成Presenter接口，Model类还是原来的Model。

###MVP的好处

- 分离了视图逻辑和业务逻辑，降低了耦合
- Activity只处理生命周期的任务，代码变得更加简洁
- 视图逻辑和业务逻辑分别抽象到了View和Presenter的接口中去，提高代码的可阅读性
- Presenter被抽象成接口，可以有多种具体的实现，所以方便进行单元测试
- 把业务逻辑抽到Presenter中去，避免后台线程引用着Activity导致Activity的资源无法被系统回收从而引起内存泄露和OOM

![](http://i.imgur.com/DbGHxaB.png)

###创建MVP的步骤
- 创建IPresenter接口，把所有业务逻辑的接口都放在这里，并创建它的实现PresenterCompl（在这里可以方便地查看业务功能，由于接口可以有多种实现所以也方便写单元测试）
- 创建IView接口，把所有视图逻辑的接口都放在这里，其实现类是当前的Activity/Fragment
- 由UML图可以看出，Activity里包含了一个IPresenter，而PresenterCompl里又包含了一个IView并且依赖了Model。Activity里只保留对IPresenter的调用，其它工作全部留到PresenterCompl中实现
- Model并不是必须有的，但是一定会有View和Presenter




