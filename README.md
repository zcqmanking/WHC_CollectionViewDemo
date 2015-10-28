# WHC_CollectionViewDemo

##  作者:吴海超
##  联系qq:712641411


## 目前独一无二封装最完美的网格菜单开源组件，支持用户行为习惯自定义菜单项位置和个数
   (用户可长按菜单项进行排序，删除，添加，自动保存用户编辑后的状态)
#具体使用方式请下载demo阅读里面很详细


###该组件支持参数自定义样式说明如下：
```objective-c
class  WHC_MenuViewParam{
    /// 缓存菜单key
    var cacheWHCMenuKey: String!;
    /// 分段标题集合
    var segmentPartTitles: [String]!;
    /// 分段图片集合
    var segmentPartImageNames: [String]!;
    /// 分段文字颜色
    var txtColor = UIColor.grayColor();
    /// 选择背景色
    var selectedBackgroundColor: UIColor!;
    /// 网格线的颜色
    var lineColor: UIColor = UIColor.lineColor();
    /// 分割视图集合
    var segmentViews: [UIView]!; // 这个属性这个版本废除不可使用
    /// 菜单视图布局方向
    var menuOrientation: WHC_MenuViewOrientation!;
    /// 每行个数
    var column = 4;
    /// 间隙
    var pading: CGFloat = 5.0;
    /// 字体大小
    var txtSize: CGFloat = 12.0;
    /// 是否能够排序
    var canSort = true;
    /// 是否能够删除
    var canDelete = true;
    /// 是否能够添加
    var canAdd = false;
    /// 是否显示页标签
    var canShowPageCtl = true;
    /// 线宽
    var lineWidth: CGFloat = 0.5;
    /// 顶部是否有线
    var isShowTopLine = true;
    /// 是否网格显示
    var isGridShow = true;
    /// 是否动态插入菜单项
    var isDynamicInsertMenuItem = false;
    /// 动态插入背景图片名称
    var insertMenuItemImageName: String!;
    /// 是否自动拉伸菜单高度
    var autoStretchHeight = false;
    /// 获取默认视图菜单配置参数
    class func getWHCMenuViewDefaultParam(titles
        titles: [String]! ,
        imageNames: [String]! ,
        cacheWHCMenuKey: String)->WHC_MenuViewParam{

        let param = WHC_MenuViewParam();
        param.segmentPartTitles = titles;
        param.segmentPartImageNames = imageNames;
        param.selectedBackgroundColor = UIColor.themeBackgroundColor();
        param.menuOrientation = .Vertical;
        param.cacheWHCMenuKey = cacheWHCMenuKey;
        return param;
    }
}

```

##运行效果一

![image](https://github.com/netyouli/WHC_CollectionViewDemo/tree/master/gif/a.gif)

####运行效果一调用方式代码如下：
```objective-c
    let menuParam = WHC_MenuViewParam.getWHCMenuViewDefaultParam(titles: ["WHC","公司通知","直销客户","渠道客户","拜访管理","拜访回馈","回馈问题","销售计划","项目报备","项目跟踪","合同管理","收款管理","工作小结","请假申请","费用申请","汇总统计","发布通知","客户审核","回馈批注","小结批注","报备审核","市场推广","售后服务","费用审核","请假审批","w","h","c","吴海超","吴","超","海","iOS","Android","WP","手机","苹果","大神"], imageNames: ["icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2"], cacheWHCMenuKey: "WHC-集合菜单样式一");

    let menuView = WHC_MenuView(frame: UIScreen.mainScreen().bounds, menuViewParam: menuParam);
    menuView.delegate = self;
    self.view.addSubview(menuView);
```

##运行效果二

![image](https://github.com/netyouli/WHC_CollectionViewDemo/tree/master/gif/b.gif)

####运行效果二调用方式代码如下：
```objective-c
    self.automaticallyAdjustsScrollViewInsets = false;
    let menuParam = WHC_MenuViewParam.getWHCMenuViewDefaultParam(titles: ["WHC","公司通知","直销客户","渠道客户","拜访管理","拜访回馈","回馈问题","销售计划","项目报备","项目跟踪","合同管理","收款管理","工作小结","请假申请","费用申请","汇总统计","发布通知","客户审核","回馈批注","小结批注","报备审核","市场推广","售后服务","费用审核","请假审批","w","h","c","吴海超","吴","超","海","iOS","Android","WP","手机","苹果","大神"], imageNames: ["icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2","icon3","icon1","icon2"], cacheWHCMenuKey: "WHC-集合菜单样式二");

    menuParam.menuOrientation = .Horizontal;  // 横向布局菜单
    let menuView = WHC_MenuView(frame: CGRectMake(0, 64.0, self.view.screenWidth(), self.view.screenHeight() - 114), menuViewParam: menuParam);
    menuView.delegate = self;
    self.view.addSubview(menuView);
```

##运行效果三

![image](https://github.com/netyouli/WHC_CollectionViewDemo/tree/master/gif/c.gif)

####运行效果三调用方式代码如下：
```objective-c
    let menuParam = WHC_MenuViewParam.getWHCMenuViewDefaultParam(titles: nil, imageNames: nil , cacheWHCMenuKey: "");
    menuParam.canDelete = false;          // 不能删除
    menuParam.canSort = false;            // 不能排序
    menuParam.isGridShow = false;         // 没有网格
    menuParam.autoStretchHeight = true;   // 自动拉伸菜单自身
    menuParam.pading = 1;                 // 间隙
    self.imageMenuView = WHC_MenuView(frame: menuView.frame, menuViewParam: menuParam);
    self.imageMenuView.delegate = self;
    self.backView.addSubview(self.imageMenuView);

    func displayCell(imagesName: [String], otherParam: AnyObject!) {
        self.imageMenuView.update(imagesName: imagesName, titles: nil);
        self.bottomView.setY(self.imageMenuView.maxY() + 1);
        self.backView.setHeight(self.bottomView.maxY());
        self.contentView.setHeight(self.backView.maxY());
        self.setHeight(self.contentView.height());
    }

```

##运行效果四

![image](https://github.com/netyouli/WHC_CollectionViewDemo/tree/master/gif/d.gif)

####运行效果四调用方式代码如下：
```objective-c
    let menuParam = WHC_MenuViewParam.getWHCMenuViewDefaultParam(titles: nil, imageNames: nil, cacheWHCMenuKey: "");
    menuParam.isDynamicInsertMenuItem = true;   // 动态插入
    menuParam.insertMenuItemImageName = "add";  // 插入图片
    imageMenuView = WHC_MenuView(frame: UIScreen.mainScreen().bounds, menuViewParam: menuParam);
    imageMenuView.delegate = self;
    self.view.addSubview(imageMenuView);

//代理：

//MARK: - WHC_MenuViewDelegate
    func WHCMenuViewClickDelete(item: WHC_MenuItem) {
        self.images.removeAtIndex(item.index);
    }

    func WHCMenuViewClickInsertItem(){
        let count = kMaxPictureChoiceNumber - self.images.count;
        if count == 0 {
            let alert = UIAlertView(title: "已选择10张,如更换图片请先长按已选图片进行删除", message: nil, delegate: nil, cancelButtonTitle: "确定");
            alert.show();
        }else {
            let vc = WHC_PictureListVC(nibName: "WHC_PictureListVC", bundle: nil);
            vc.delegate = self;
            vc.maxChoiceImageNumber = count;
            self.presentViewController(UINavigationController(rootViewController: vc), animated: true, completion: nil);
        }
    }

    //MARK: - WHC_ChoicePictureVCDelegate
    func WHCChoicePictureVC(choicePictureVC: WHC_ChoicePictureVC!, didSelectedPhotoArr photoArr: [AnyObject]!) {
        if photoArr != nil {
            for (_ , image) in photoArr.enumerate() {
            self.images.append(image as! UIImage);
            }
            self.imageMenuView.insertMenuItemsImage(self.images);
        }
    }

```
