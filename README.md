# LiuPN---blog
LiuPPN的github的blogs


可能在百度出的一些博客上，会看到：


这些指令，但是，在最后这条指令过后可能会报这样的错误：



ERROR | xcodebuild: Returned an unsuccessful exit code. You can use ‘—verbose’for more information
…fatal error: ‘UIKit/UIKit.h’file not found
…fatal error: ‘XCTest/XCTest.h’file not found 

解决办法：
1、打开注释s.ios.deployment_target = “5.0”  UIKit问题解决掉了
2、在podspec文件里面，将注释打开s.frameworks = "Foundation", "UIKit", “XCTest”并写上这两个框架即可，XCTest问题解决掉了
再次：
$ pod lib lint
-> PNPopBottomMsg (1.0.0)
PNPopBottomMsg passed validation.
成功了！

【下面是 podspec内容（$pod spec create PNPopBottomMsg），其中不重要的注释给删除掉了：】
Pod::Spec.new do |s|
  s.name         = "PNPopBottomMsg"
  s.version      = "1.0.0"
  s.summary      = "A pop bottom tip view of PNPopBottomMsg."
  s.description  = <<-DESC
A pop bottom tip view of PNPopBottomMsg.And you do not worry the width and height of the pop tip view.
                   DESC
  s.homepage     = "https://github.com/LiuPN/PNPopBottomMsg"
  s.license      = "Apache"
  s.author             = { "liupanniu" => "panniuliu@139.com” }
  s.ios.deployment_target = "5.0"
  s.source       = { :git => "https://github.com/LiuPN/PNPopBottomMsg.git", :tag => "1.0.0" }
  s.source_files  = "PNPopBottomMsg", "PNPopBottomMsg/**/*.{h,m}"
  s.exclude_files = "PNPopBottomMsg/Exclude"
  s.frameworks = "Foundation", "UIKit", "XCTest"
end

这是遇到的问题，其他步骤可参考：
http://blog.csdn.net/wzzvictory/article/details/20067595
