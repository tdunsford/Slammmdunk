$:.unshift("/Library/RubyMotion/lib")
require 'motion/project'
require 'rubygems'
require 'motion-cocoapods'

Motion::Project::App.setup do |app|
  # Use `rake config' to see complete project settings.rake
  app.name = 'Slammmdunk'

  app.provisioning_profile = 'MarkDev.mobileprovision'
  app.sdk_version = "5.0"

  app.frameworks << "QuartzCore"
  app.frameworks << "CoreText"

  app.icons = ["Icon@2x.png"]

  app.info_plist['UIStatusBarStyle'] = "UIStatusBarStyleBlackOpaque"
  app.info_plist['UIPrerenderedIcon'] = "true"

  dirs = ['bubblewrap','sugarcube', 'teacup', 'styles', 'app']

  app.files = dirs.map{|d| Dir.glob(File.join(app.project_dir, "#{d}/**/*.rb")) }.flatten
  app.files_dependencies './app/app_delegate.rb' => './app/MCNavigationController.rb'

  app.vendor_project( "vendor/PFGridView", :xcode,
  :xcodeproj => "PFGridView.xcodeproj", :target => "PFGridView", :products => ["libPFGridView.a"],
  :headers_dir => "PFGridView")
  
  app.vendor_project( "vendor/WEPopover-lib", :xcode,
  :xcodeproj => "WEPopover-lib.xcodeproj", :target => "WEPopover-lib", :products => ["libWEPopover-lib.a"],
  :headers_dir => "WEPopover-lib")

  app.vendor_project( "vendor/SVPullToRefresh", :xcode,
  :xcodeproj => "SVPullToRefresh.xcodeproj", :target => "SVPullToRefresh", :products => ["libSVPullToRefresh.a"],
  :headers_dir => "SVPullToRefresh")

  app.pods do
    dependency 'Nimbus/Core'
    dependency 'Nimbus/AttributedLabel'
  end
end
