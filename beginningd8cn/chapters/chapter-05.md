#第5章 内容类型
当你问Drupal开发者，Drupal最强大的特性是什么? 许多人将会说是它可以自定义内容类型的能力。 那什么是内容类型呢? 你可以把内容类型看做一个模板,通过这个模板用户可以在你的网站上编辑内容。你可以选择Drupal 内核中已经有的内容类型比如"Basic page" 或者 "Article" 来满足你网站的所有需要 。但是，很多时候你需要是使用自定义内容类型来更多的控制用户如何输入信息,或是输入的信息以何种方式显示在网站上。 这一个章节,将会从零开始向你展示自定义一个内容类型是多么的简单 ! 请找一个舒适的环境，带上你自己,开始我们新的旅程吧 !
## 5.1 基本页面和文章内容类型
当你安装Drupal 8的时候，你会自动获得两个由维护团队定义的Drupal内置内容类型：基本页面和文章。当你通过“基本页面”内容类型来编辑一段内容时,你会发现它包含了两个基本字段:标题和正文。

一个作者通过使用基本页面可以很容易的输入标题(红色星号标注表示必填字段)和正文字段的内容文本。 并且,内容页面很灵活,它支持一般著作所需的任何类型:

* 使用HTML渲染一整本书 (包含标题,表格,CSS等)
* 插入一个图片
* 写一个句子

“文章”内容类型和“基本页面”内容类型很像,它还支持上传独立的图片作为一个独立的元素,比如文章中经常使用的横幅图片(并非嵌入到正文区域内),还定义了一些用来对文章进行归类的标签（第四章详细解释如何对内容进行分类）。

类似于“基本页面”,文章类型可以用来创建有关任何主题的内容,并且正文区域(body)支持任何格式的文本。

尽管“基础页面”和“文章类型”基本上满足了通常的内容。但是仔细想想,在一些情况下你想对所获得的信息提供一些其他结构的格式，比如下面这些情况:

* 需要在作者发布内容之前补充一些特定的信息: 比如事件发生的日期、时间、地点甚至是Google Map的链接
* 具备基于某个内容项信息的计算能力
* 具备按照某个字段排序的能力
* 具备基于某个字段的值过滤或者限制某些内容项在网页上显示的能力
* 具备控制内容项在页面中如何显示的能力:比如你要按照标题,作者,ISBN,价格,书籍描述的顺序显示一本书的详细内容。

假如你只能通过基础页面和文章发布你的所有内容，并且还要赋予它排序,过滤,,声明必须字段,计算，控制一个内容项如何显示,想想该有多困难啊! 很幸运,Drupal提供了自定义内容类型的能力让以上这些都成为可能,并且还有其他你想不到的功能等待你的发现 。
## 5.2 自定义内容类型的定义
一个自定义的内容类型在基于基础页面和文章内容类型基础上可以被你或者Drupal管理者进行定义,并且由Drupal 8核心模块支持。

为了显示自定义内容类型的灵活性,我们来创建一个关于获取即将来临的事件的信息的内容类型。 这个事件也许是一场音乐会、一场戏、一堂课、一个游戏或者是其他提前规划的任何活动。

  当编辑一个事件的详细信息的时候,你也许希望包含以下细节:

* 事件的名称或者标题
* 事件开始的日期与时间
* 事件结束的日期与时间
* 事件发生的地点
* 事件的相关介绍
* 参与事件的花费

等会你会发现,Drupal给我们提供了非常简单易用的用于创建和修改自定义内容类型的管理界面。并且,当你创建了自定义内容类型之后,拥有相关权限的用户就能针对此内容类型进行编辑、发布和删除等操作（Drupal通过用户角色来限制用户对自定义内容类型的权限）。

## 5.3 自定义内容类型的创建
### 5.3.1 基本内容填写和设定
创建自定义内容类型需要两个步骤：
1. 列出所需信息的类型
2. 使用Drupal管理页面创建自定义内容类型

这里我们按照上一章节列出来的信息类型，创建一个“事件”自定义内容类型。

首先,点击管理页面子菜单中的管理菜单、结构菜单。在结构页面（如图5-1所示），点击“内容类型” (/Structure/Content types）

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/content_type.png)
 
图 5-1 结构页面的“内容类型”链接

"内容类型"页面（如图5-2所示）列出了所有的已存在的内容类型,就是我们所提到的Drupal内置的的“文章”和“基本页面”内容类型。"内容类型"页面可以创建新的内容类型。点击"添加内容类型"(Add content type) 按钮,开始添加我们的“事件”内容类型。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/add_content_type.png)

图5-2, 内容类型列表


当你点击"添加内容类型"(Add content type)按钮后,出现的第一个界面是定义新的内容类型的一般属性的一个表单(如图5-3所示)。这个表单包括：一个标题(Name)属性字段,一个描述(description)字段（这个描述字段用于让作者创建新的内容）,一个标题的标签(label)属性字段,还有其他一些我们稍后详细介绍的其他配置选项。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/add_content_type_detail.png)

图5-3 内容类型创建表单

按以下的步骤创建内容类型:

* 填写内容类型的名称(Name): 在这里我们填入"Event",当我们为一个新的内容类型创建名称时，应该遵循Name字段下面的指导信息。
* 提供该内容类型如何使用的描述信息 : 比如"一个用于记录将要发生的事件的内容类型"。
* 将标题的“标题的标签”(Title field label) 从改成"事件的名称"(Event title),这能够给使用此模板创作事件信息的作者更加直观的理解。
* 把"在提交之前预览"(Preview before submitting) 设置为可选项。
* 提供清晰的提交指南 : 这个一个可选项, 并非一定要填写! 在这里，我们可以填写"请在提交之前填写完整所有必填项"作为提交指南,在创建内容类型的时候你可以选择使用或者忽略这个字段。

当你创建一个新的内容类型时，还有其他需要你仔细考虑的可选设置项。
### 5.3.2 发布设定
首先是左边菜单栏的发布选项(Publish options) 你可以点击它(图5-4)
![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/publish_options.png)

图5-4 发布选项
</br>
</br>

你可以按照自己的意愿设置你是否想自动发布(一保存就可在网站中看见)，和是否自动显示在网站的首页上，你可以自己调整这些选项。对于我们创建的“事件类型”,我们想在保存的时候自动发布,但是不想它们自动发布在首页上。因此,我们取消选择"Promoted to front page"单选框,我们也可以设置一个事件是否固定在列表的首行(如果有多个内容类型,事件类型总是在首行)。此外,我们想在作者更新事件内容的时候创建一个新的版本(通常是一个好想法,但是取决于你是否在之后的某些时候想看到曾经你改动过什么,或者是当目前的版本错误的时候恢复到之前的版本)。对于我们的事件类型,我们选择"创建新版本"(Create new revision)复选框。

### 5.3.3 显示设置
接下来是显示设置。点击左侧的“显示设置”（Display settings）选项卡,你将会看到相关可用的配置(图5-5),你可以设定Drupal 是否显示作者的名字和创建的时间。在这里我们认为显示作者和时间并不相关,所以我们取消选择这个单选框。你当然可以根据自己编辑的内容类型决定是否要显示作者的名字和内容发布的时间。如果相关，你可以勾选这个复选框。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/display_settings.png)

图5-5 显示设置

### 5.3.4 菜单设置
最后一个选择是关于呈现给作者的菜单参数的设置。 点击“菜单设置(Menu setting)” 选项卡可以显示出相关的菜单参数（图5-6）. “可用的菜单”展示出这个内容类型可以展示在哪些菜单的下面。 在内容创建期间,作者可以选择正在创建的内容项是否出现在被选择的菜单中。图5-6显示的案例中,只有“主导航栏(Main navigation)”是可以被内容作者选择的。你可以取消选择主导航栏，用以隐藏所有可以被选择的菜单列表，或者也可以选择不止一个菜单，允许作者选择多个菜单。 “默认父菜单 (Default parent item)” 允许你设置当用户在利用你的新的内容类型创建与此类型对应的内容项时，哪一个菜单可以在“菜单设置”页面被自动选择。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/menu_setting.png)

**图5-6** 菜单设置

在我们的例子中,我们保留默认值，点击“保存和管理字段(Save and manage fields)”按钮。

Drupal 现在显示的是“管理字段(Manage field)”页面 (图5-7)

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/manage_field.png)

图5-7.事件类型的“管理字段”页面
## 5.4 自定义内容类型
接下来，我们就可以根据我们的事件类内容型创建新的事件。但是,事件内容类型只包含两个字段：事件标题和正文。 而我们需要事件描述，开始时间，结束时间，地址,座位类型,会场是否提供协助,事件类型以及是否提供一份可被网站访问者下载的文件(比如一个程序)。正如在图5-8中显示的，Drupal自动创建了我们将会用于事件描述的正文字段。 

### 5.4.1 事件描述正文字段便签的改变
![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/changing_label.png)

图5-8. 改变标签字段


我们通过修改正文字段的标签----“正文(Body)”字段的标签改为"事件描述(Event description)"，这样我们创建了一个更好的方便人们理解的事件文本类型的指示符。点击“正文(body)字段”的编辑按钮,在标签(Label)字段，将“正文(body)”改为"事件描述(Event descripttion)" （见图5-8）,然后表单底部的点击“保存设置(Save settings)”按钮。
保存更新的正文标签后,Drupal将会跳转到修改标签后的"管理字段（manage fields）"页面,见图 5-9。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/revised_field.png)

图5-9. 修订字段标签



### 5.4.2 添加开始时间字段
	
点击 “添加字段(Add field)”按钮,下一步是选择添加什么类型的字段,或者是添加已经存在的字段到这个内容类型。一个之前在其他内容类型创建的字段可以在新创建的内容类型中重用,而不用重新创建字段,相当于我们可以在列表中选择已经存在的字段重用该字段的定义。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/add_field.png)

图5-10. 选择字段类型


点击“时间类型（Date）”后,在屏幕上，你将会被提示输入新字段的标签。这个标签显示在内容编辑表单中，以便于作者可以知道当内容项目呈现在网站上时，他们要为哪一个字段输入一个值，哪一个字段是要呈现给最终用户的。 
因为我们创建的是事件的开始日期,在标签字段中输入"开始日期(Start Date)"， 然后点击 "保存并且继续（Save and continue）" 按钮。

在字段创建过程中，接下来是设置时间字段的格式，是日期和时间格式或者是仅有日期,还有该字段允许取值的数量 (见图5-11)。 通常一个事件往往只对应一个时间,因此我们将“日期类型(Date type)”选项设置为“日期和时间(Date and time)”,将“允许的值数量(Allowed number of values)”选项设置为“限制(Limited)”并且"1",因为我们的事件仅仅发生一次。 你会发现"允许的值数量"配置选项将会出现在创建的每一个字段中中,你也许会碰到用户针对一个字段可以取多个值的权限的情况。比如，将来同一个事件会发生多次。那么我们可以设定"允许的值数量"为大于1的数,那么在我们创建该类型的内容时，将会产生对应数量的该字段的输入框。 如果你设置为"不限制",那么用户将会字段下面的通过“添加(add another)”按钮随意创建一个值。 因此在创建字段之前我们需要想清楚该字段具体什么作用,然后设置"允许的值数量"。许多情况下，也许 1 并不是最好的解决方案。 然而，在这个例子中，我们设置的值为1。点击"保存字段设置(Save field settings)"按钮继续下一步。


![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/setting_date.png)

图5-11. 设置日期类型和允许取值的数量

Drupal 显示的下一个表单（图5-12所示）可以使你设置关于事件开始日期字段的更多详细参数。在这个表单中你可以设置:

* 修改之前这个字段预定义标签的内容。除非之前定义的内容错误的或者你改变了想法,否则你可以使用默认显示的。
* 在"Help text"字段中输入相关的帮助信息。这是一个描述输入这个字段的数据要求的字段,比如需要用户输入mm/dd/yyy格式的日期. 这是一个可选的字段。
* 定义这个字段是否为必选字段。 一个必选字段将会用红色星行标注,Drupal 将会在内容项目保存前强制用户输入这个字段的值。因为我们的内容类型是关于事件,日期对于事件是非常重要的字段,因此我们将会选择"Required field"单选框。
* 定义显示给用户的这个字段是否为一个默认值。 因为我们的字段处理的是将来的某个日期,提供一个默认的值没有意义。当然很多情况下，对于某些字段是很有意义的,比如选择一个默认的座位，你也许会希望设置为默认值：最好的。在这些情况下，这些地方你是需要设置默认值的。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/setting_date2.png)

图5-12. 设置事件开始日期字段的详细参数

点击"保存设置(Save settings)"按钮完成开始日期字段的设置,Drupal将会重新显示已经添加了开始日期字段(Start Date)的事件的“管理字段(Manage field)”页面(见图5-13)。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/manage_field2.png)

图5-13.包含开始日期字段的事件内容类型的字段列表

现在我们添加之前定义的其他字段: 结束时间,事件描述,和事件地址. 按照之前的相同步骤来创建结束时间字段。当创建事件地址的时候,选择"文本(formatted,long)" 为字段类型,代替“日期（Date)"类型 ，因为事件地址的输入值将会是一段或者两段文本。当你完成后，你的列表将会类似于图5-14。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/event_List.png)

图5-14.事件内容类型的所有字段列表


现在我们的事件类型已经准备好可以使用了。为了测试我们创建的新的类型,点击左上角的“返回站点(Back to site)"按钮并且点击"添加内容(Add Content)"链接,我们将会看到在网站上可用的内容类型列表。

我们的事件类型显示在可用的内容类型列表中。点击事件内容类型,可以看到事件内容类型创建页面（见图5-15）。 这个页面显示了事件标题,事件描述,开始时间,结束时间,事件地址.


![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/new_event.png)

图5-15.创建一个新的事件的表单


使用事件创建表单创建一个事件类型的样例。当你输入完所有的值后,点击"保存并发布(Save and publish)" , Drupal 将会使用你自己输入的特定的值显示新的事件内容项目。在图5-15中输入值之后的事件样例，将会作为一个新的事件显示在图5-16中。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/content_view.png)

图5-16 完整的样例事件

## 5.5 其他字段类型

在我们的事件内容类型中,我们创建了一些方便用户输入日期和地点的字段。这里有一些比使用文本字段类型更加有效的字段类型：

* 单选按钮(Radio buttons): 给用户提供一系列的选择,但是仅能选择其中一个。
* 复选框(Check boxes) : 为用户提供了可选择列表，允许用户选择列表中的一个或多个值。
* 选择列表（Select list） : 特别长的选择项目列表；比如世界上的所有国家。
* 文件上传(File upload) : 当你想给某块内容上传和添加附件时，可以使用这个字段。
* 图片上传(Image upload): 当你想上传并显示图片时，可以使用这个字段。
* 文本区域(Text area) : 提供输入一个段落,它将会提供一个可以输入多行的文本框,text 字段只能提供单行的文本输入
* 数值字段(Numeric field) : 当你想输入数字时，使用这个字段。
* 实体参照字段(Entity reference fields) : 用于想把创建的这个内容项目与其他内容项目关联时使用这个字段。例子之一就是你的网站有一个叫包含头像和个人简历的关于表演艺术家的“Biography（传记）”内容类型。如果你想在一个事件内容项目中包含有关于一个艺术家的头像和个人简历的信息，你可以使用实体参照字段与这个艺术家的传记事件进行链接，从现有的内容项目显示这个艺术家的头像和个人简历，而不用必须手动重新链接到这个事件的个人简历信息。
* 术语参照字段（Term reference field） : 如果你想让你的内容项目包含分类术语，可以使用这个字段。

以上列出的这些字段类型全部是Drupal 8核心模块。 还有一些自定义的字段类型可以在贡献模块中找到,你可以在 www.drupal.org/project/modules 页面,通过选择字段项目在"Module categories"过滤,然后开始搜索。你将会找到很多扩展模块，提供许多额外功能，类似于其他字段类型。通过第12章描述的过程，你可以安装扩展模块。

当你创建新的内容类型的时候，你很有可能会遇到需要使用其他字段类型中的任何一种。我们将会通过使用其他的字段类型增加许多其他的字段，来扩展我们的事件内容类型。
### 5.5.1 单选按钮与复选框(Radio Buttons & Check box)
1. 如图5-17,首先我们添加list

当你想给用户呈现一系列他们可以选择其中一个作为取值时，单选按钮是非常有用的（允许用户选择列表中的一个或多个值时，复选框是有用的）。我们扩展我们的事件内容类型，使其能够选择事件中可用的座位类型：预定作为或者普通入场券。点击页面顶端的“管理”和子菜单中的“结构”，选择“内容类型”和“事件内容类型”的“管理字段”菜单。点击“添加字段”按钮开始这个过程。图5-17显示了这个字段类型列表。由于我们创建的是一个单选按钮列表，选择“列表（文本）”选项。选择“列表（文本）”选项后，将会出现一个标签字段。在标签字段输入“座位类型”，接着点击“保存并继续”按钮。

![radio_buttons](http://work.beiweng.org/d/file/drupal/chapter5/2016-04-08/03effcb355bd3630bf41f53d5da21197.png)

图5-17. 添加列表字段


2.如图5-18,枚举列表的值

这个过程的下一步是提供将会出现在列表中的值（如图5-18）。在这个界面我们必须指定“允许的值列表”，这将会是呈现给用户的可选列表。Drupal
要求以 key | label 这样的格式枚举每一个值,其中被选中的key将会被存储到数据库中,而label 将能够被用户看到。在图5-18的例子中，我使用“预定座位”和“普通入场券”导致生成的存储在数据库中的值是预定座位或者普通入场券。通过设置 "允许的值数量(Allowed number of values)" 等于1时,表现为单选框,用户只能选择一个值。当大于1时表现为复选框。在选择值后，点击“保存字段设置”按钮继续这个过程。

接下来的步骤是这个字段的配置过程，如图5-19所示。在这个表单中我们可以：

* 改变标签。
* 创建帮助文本。
* 标记字段为必备字段。
* 设置呈现在网页上默认选择的默认可选项。

输入帮助文本可以帮助浏览者理解这个字段是干什么的，可以设置普通入场券为默认值，当创建事件网页的时候可以自动被选择。设置这个值之后，点击“保存设置”按钮。

这个过程的最后一步是定义我们想要Drupal如何显示值列表，要么是“选择列表”，要么是“复选框/单选按钮”。如果你设置“允许的值数量”为1，选择列表将会以下拉列表显示，使用户可以选择唯一的值。如果你设置“允许的值数量”大于1，所有值的列表将会全部显示，而不是下拉式列表。如果你设置“允许的值数量”为1，列表将会以单选按钮显示；如果你设置“允许的值数量”大于1，列表将会以复选框显示。点击“管理字段”（见图5-20）页面顶部的“管理表单呈现”菜单可以设置使用什么类型的插件来显示座位列表类型。在这个内容类型的字段列表中查找座位字段类型，将插件栏从“选择列表”修改为“复选框/单选按钮”。点击保存按钮来保存你的修改。
 
在点击保存按钮后，如图5-21所示，这个新的字段就可以使用了。你会注意到在列表中Drupal新增了第三个可选项，默认选项（N/A）。由于我们勾选“必备字段”的复选框（见图5-19），Drupal回自动插入默认选项，因为一个访问者也许希望不选择任何一个选项。如果你想清除默认选项，勾选“必备字段”复选框，Drupal将会自动从列表中清除这个选项。

复选框类似于单选按钮，但是允许用户从列表中选择多个值。我们现在通过新增用以解决残疾人出席者的可用设施问题复选框列表来扩展我们的事件内容类型。我们将会创建复选框，指定助听设备、视觉辅助设备轮椅座位在事件中是可用的。为了定义复选框列表，返回事件内容类型的“管理字段”页面，点击“添加字段”按钮。从“添加新的字段”选择列表中（参照图5-17）选择“列表（文本）”，在标签字段中输入“辅助设备”标题（见图5-22）。

点击“保存并继续”按钮后，输入三个可选项的值，如图5-23所示，将“允许的值数量”从限制修改为不受限，允许访问者可以从列表选择一个或多个值。点击“保存字段设置”按钮继续。
 
接下来的一步是输入帮助文本用以指导用户可以通过辅助设备字段做什么，有必要的话可以设置字段为必备字段，也可以设置默认值（见图5-24），点击“保存设置”按钮。以我们的例子为例，我们没有将辅助设备为必备字段，也没有设置默认值，因为大部分对我们事件的访问者可能不需要辅助设备。

在完成辅助设备字段的设置后，你必须设置Drupal以“复选框/单选按钮”的形式显示此字段。点击内容编辑表单顶端的“管理表单显示”菜单，将“选择列表”插件形式修改为“复选框/单选按钮”形式，点击保存按钮。为了查看添加这个字段后的结果，点击“添加内容”链接新增一个事件。新的复选框字段如图5-25所示。

### 5.5.2 选择列表(Select List）

选择列表也称为下拉列表。为了显示选择列表，我们为事件内容类型创建了一个新的字段，下拉列表列出了这个事件是一场音乐会、一场话剧还是一场演讲。创建一个选择列表类似于之前创建的字段类型。在事件内容类型的“管理字段”页面，点击“添加字段”按钮。字段类型选择“列表（文本）（参照图5-17）”，在标签字段输入"事件类型"。在设置这些值之后，点击“保存并继续”按钮继续对你的新的选择列表字段进行定义。

在接下来的界面中，如之前的例子所示，为列表中的每一个可选项输入一对“key|label"值。在“允许的值列表”每行中分别输入concert|Concert, play|Play, and lecture|Lecture（参照图5-18）。设置默认的“允许值数量”为“限制”和“1”。点击“保存字段设置”继续。在下一步的配置界面，在你设置好你想改变的值之后，点击“保存设置”按钮。

在之前的例子中，我们必须点击“管理表单显示”菜单，将“选择列表”插件形式修改为“复选框/单选按钮”形式。由于我们想要显示选择列表形式，所以就没有必要改变。现在可以使用新建的选择列表字段。图5-26显示了当新建一个事件时，在前面的步骤中所定义的选择列表是什么样子的。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/select_list.png)

图5-26.选择列表


### 5.5.3 文件上传
文件上传字段类型提供了一个文档浏览器按钮，允许一个用户浏览本地计算机的文件上传到Drupal，附加到他们创建的内容项目中。创建一个文件上传字段几乎与创建其他字段类型的过程是一样的。我们将会扩展我们的事件内容类型，事件内容类型将会包含事件的大纲。跟之前的字段一样，导航到事件内容类型的“管理字段”页面，点击“添加字段”按钮。

在“添加字段”页面（参照图5-17），选择“文件”作为字段类型，在标签字段输入“事件项目”。点击“保存并继续”进行下一步。在“字段设置”页面（见图5-27），勾选“显示字段”复选框和“默认显示文件”复选框。勾选这些复选框，当访问者浏览内容项目的时候，给作者提供了显示一个文件的链接。按照默认方式，上传文件的目标路径是“Public files” 网站管理者定义的配置目录。（我将会在第十四章详细介绍配置选项。）接下来，在“允许的值数量”字段，设置内容作者启用的文件上传的数量。我们将这个选项设置为“limited”和“1”，因为我们能预测到每个事件只允许内容用户上传一个活动项目文件。根据您的要求，你也可以修改允许上传文件的数量。在表单中设置好值以后，点击保存字段设置按钮。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/file_upload.png)

图5-27.设置文件上传参数

在最后一步设置中（见图5-28），你将会发现解释这个字段用来干什么的帮助文本的字段和选项（在我们的例子中是“上传事件项目”）表示了是否一个上传文件在创建一个事件时是必备的（在我们的例子中未勾选），规定了允许的文件扩展名（在我们的例子中我们允许上传txt, doc, docx, ppt, pptx, or pdf文件扩展名的文件），在公共文件目录中选择性地识别相应的目录进行文件的上传，设置“最大上传大小（例如在我们的例子中允许最大的文件达到1M）”,内容作者使用描述字段来描述这个文件。一旦你更新了这个值，点击表单底端的“保存设置”按钮。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/file_configure_more.png)

图5-28文件上传设置参数

图5-29显示了事件创建表单上的新文件上传字段。

### 5.5.4 文本区域


可能会出现这样的情况：您希望在内容创建表单上提供一个字段，以使作者能够输入段落或更多的文本。 虽然您可以通过文本字段（单行文本输入框）提供此功能，但更容易接受和标准的方法是提供文本区域。 扩展我们的事件示例，让我们添加一个新的字段，用于捕获到场地的驾车路线。 要创建文本区域，请按照我们在上一节中用于创建其他字段的步骤操作。 单击事件内容类型的“管理字段”页面上的“添加字段”按钮，然后从“添加新字段”选项列表中选择“文本（格式化，长）”（参见图5-17）。 在标签字段中输入“行车路线”，然后点击“保存并继续”按钮。

下一个窗体允许您设置将为此字段创建多少个文本框。 将值设置为1，然后单击“保存字段设置”按钮。下一个窗体提供了输入帮助文本，根据需要设置字段，指定默认值以及定义作者将启用哪种类型的文本处理选项。选择完整HTML允许作者使用WYSIWYG编辑器的全部功能，而基本HTML将可用格式选项的数量限制为基本（参见图5-30有限HTML选项）。 选择基本HTML，然后点击“保存设置”按钮。 新字段现在可供使用。 尝试创建新事件，您将看到新的文本区域，您可以在其中输入行车路线（见图5-30）。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/text_area.png)

图5-30 用于驾驶路线的新文本区域


### 5.5.5 数值字段和其他字段类型
通过遍历前面列出的各种字段类型，你可以看到，我们创建的几乎每个字段类型都有一个模式和一组常用参数。数值字段本质上是一个文本字段，但是由Drupal自动限制，以便它只接受数字字符（0-9）。当你通过下载和启用贡献的字段模块来扩展字段类型时，你会发现与你正在创建的字段的结构过在创建过程上有轻微的变化。但是，整个过程将是相同的。如果您还没有这样做，现在是浏览可用于扩展Drupal 8内核中可用的字段模块列表用以扩展Drupal功能的完美时间。访问http://drupal.org/project/modules，点击“模块类别”过滤器中的字段项，然后点击搜索。当你浏览时，确保浏览的是为Drupal 8构建的字段模块，因为字段中许多固有的功能现在是Drupal核心的一部分，而在以前的Drupal版本中，您必须下载并安装CCK，才能完成我们刚刚使用Drupal完成的。要将列表缩小到只有Drupal 8，请从Core compatibility下拉列表中选择8.x，然后单击Search按钮。

### 5.5.6 格式化自定义内容的输入形式
有时，你可能会发现，您的新内容创建表单的视觉表示并不是你希望的显示方式。 你可能想更改表单上字段的顺序，用于在字段中创建内容的窗口小部件的类型或窗口小部件本身的格式。要更改表单的显示方式，请按照先前执行的步骤编辑内容类型。 单击页面顶部的“管理表单显示”选项卡，将显示其窗口小部件类型和窗口小部件配置的字段列表（请参见图5-31）。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/manage_display.png)
  
图5-31.“管理表单显示”选项卡

要重新排列窗体上字段的顺序，请单击并按住要移动的字段旁边的箭头图标，将该字段拖动到希望显示的位置，然后释放鼠标按钮。要更改窗口小部件类型，只需从窗口小部件选择列表中选择一个新值，然后更改窗口小部件的外观（例如，更改文本区域以显示超过默认的五行），请点击齿轮右栏图标（见图5-31）。

例如，让我们将驾驶路线的文本区域字段从​​默认的五行文本更改为十行文本。为此，请点击“驾驶路线”字段右侧列中的齿轮图标。表单将展开以显示一个字段，你可以在其中更改行数，以及输入将出现在字段中的占位符文本，直到作者开始在该字段中输入文本。将行数从5更改为10，然后单击更新按钮，然后单击保存按钮。创建新事件时显示的行数为十，为作者提供更多输入路线的空间。
### 5.5.7 格式化自定义内容的输出

有时，您向网站的最终用户显示的新内容类型的视觉表示与您希望在屏幕上使用新内容类型创建的内容的呈现方式不符。在上一节中，我们考虑重新排列内容作者用来创建事件的表单上的字段;在这种情况下，我们重新排列呈现给最终用户的事件的内容字段。 

通过单击自定义内容类型编辑表单上的“管理显示”选项卡，可以实现与字段有关的标签的顺序和位置的调整。

我们将使用我们的事件内容类型来演示功能。单击“管理显示”选项卡将显示如图5-32所示的页面。

![](http://llwoll.github.io/2016/04/20/Drupal-%E5%86%85%E5%AE%B9%E7%B1%BB%E5%9E%8B/manage_display2.png)

图5-32 “管理显示”页面

此页面列出了与我们的内容类型相关联的所有字段，并且提供了为每个字段定义标签和内容的基本显示属性的功能。默认情况下，我们可以设置两组值：一组用于默认（完整节点），一组用于摘要视图。默认选项显示完整的内容项，摘要显示只显示内容项的标题和正文字段的修剪版本。你可以使用页面左上方的两个链接在二者之间切换。如果单击每个字段的标签的选择列表，您会发现有三个选项：
* Above上方：标签将显示在您为字段选择的窗口小部件上方。
* Inline内联：标签将显示在窗口小部件的左侧，与窗口小部件在同一行上。
* Hidden隐藏：标签不会显示在屏幕上。

 
如果单击每个字段的格式的选择列表，将根据字段类型找到一些选项。对于文本相关字段，选项是

* 缺省：内容将按您创建字段时指定的方式呈现在屏幕上。
* 摘要或修剪：如果字段类型具有摘要值和正文值，将显示摘要值。如果没有摘要，则正文值将被修剪为指定的长度。
* 裁剪：内容将被“裁剪”到指定的字符数。如果内容长度超过指定的字符数，将显示“阅读更多”链接。
* 隐藏：内容不会出现在屏幕上。

对于其他字段类型，选项取决于正在显示的内容的类型。

要重新定位字段，请单击并按住要移动的项目的字段标签旁边的箭头图标，将该字段拖动到希望显示的位置，然后释放鼠标按钮。记住在将所有字段移动到正确位置后，单击保存按钮。

我们还可以定义内容如何显示超出默认值和Teaser的其他模式，如RSS，搜索索引和搜索结果。要启用这些模式，只需点击管理显示页面底部的“自定义显示设置”链接以展开列表，然后从模式列表中选择。启用其他模式后，例如，事件显示在搜索结果页上时，你可以定义内容的显示方式。
 
你还可以定义自己的模式，可用于在各种情况下以不同方式显示内容。要创建新的视图模式，请访问“结构”➤“显示模式”➤“视图模式”，然后单击“添加新视图模式”按钮。从选项列表中选择内容，系统会在提示时为您的视图模式命名（例如，精选）。一旦创建了新的视图模式，您就可以在管理显示页面上使用该模式来定义该视图模式的唯一输出。

## 总结 

内容类型是Drupal杀手级应用之一,也是一个我们需要深入理解的重要的概念。虽然您可以只使用基本页面和文章内容类型构建一个Drupal网站，但是您可能希望通过使用自定义内容类型提供的功能和功能。在本章中，我只演示了为我为客户构建的几乎每个网站创建的自定义内容类型之一。我经常使用的其他自定义内容类型包括客户，产品，部门，常见问题，位置和员工。在您设计和开发新网站时，我确定你将识别一个或多个您可以使用的自定义内容类型。

自定义内容类型的另一个强大的功能是能够开发存储在Drupal数据库中的自定义内容类型数据的自定义报告或“视图”。如果你考虑本章中创建的事件内容类型，生成按开始日期排序的事件列表或按地点排序的列表可能很有用。

下一章提供Drupal主题的概述。我们的模块之旅顺利完成,请抽空多多实践 ,毕竟孰能生巧,谢谢你的阅读 。 