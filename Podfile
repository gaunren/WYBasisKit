platform :ios, '13.0'
inhibit_all_warnings!
use_frameworks!
#use_frameworks! :linkage => :static：
use_modular_headers!

# 使用Cocoapods清华源
source 'https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git'

# 使用Cocoapods官方源
#source 'https://github.com/CocoaPods/Specs.git'

# 加载脚本管理器
require_relative 'PodFileScripts/Podfile'

# 选择设置选项（三选一）
# configure_settings_option(SETTING_OPTIONS[:pods_only])    # 只设置Pods项目
# configure_settings_option(SETTING_OPTIONS[:user_only])    # 只设置用户项目
configure_settings_option(SETTING_OPTIONS[:all_projects])   # 设置所有项目(默认)

# 设置Pods项目版本(仅限从Podfile解析部署版本失败时有效)
#set_pods_deployment_target('13.0')

workspace 'WYBasisKit.xcworkspace' # 多个项目时需要指定target对应的xcworkspace文件

target 'WYBasisKit' do
  project 'WYBasisKit/WYBasisKit.xcodeproj' # 多个项目时需要指定target对应的xcodeproj文件
  pod 'AFNetworking'
  pod 'MJRefresh'
  pod 'PureCamera'
  pod 'Masonry'
  # 根据Xcode版本号指定三方库的版本号
  if xcode_version_less_than_or_equal_to(14, 2)
    pod 'SDWebImage', '5.20.1'
  else
    pod 'SDWebImage'
  end
end

project 'path/to/Project.xcodeproj'
target 'WYBasisKitVerify' do
  project 'WYBasisKitVerify/WYBasisKitVerify.xcodeproj' # 多个项目时需要指定target对应的xcodeproj文件
  pod 'WYBasisKit-oc', :path => 'WYBasisKit/WYBasisKit/WYBasisKit'
  pod 'Masonry'
  # 根据Xcode版本号指定三方库的版本号
  if xcode_version_less_than_or_equal_to(14, 2)
    pod 'SDWebImage', '5.20.1'
  else
    pod 'SDWebImage'
  end
end

post_install do |installer|
  apply_selected_settings(installer)
end
