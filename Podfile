source 'https://github.com/CocoaPods/Specs.git'
source 'https://github.com/Artsy/Specs.git'
workspace 'TangramKit.xcworkspace'

def pods
  pod 'LookinServer', :configurations => ['Debug']
end

inhibit_all_warnings!
ENV['SWIFT_VERSION'] = '5.0'
targets = ['TangramKitDemo']
targets.each do |t|
    target t do
      use_frameworks!
      platform :ios, '12.0'
      project 'TangramKit.xcodeproj'
      pods
    end
end

#target 'TangramKitDemo' do
#  use_frameworks!
#  platform :ios, '12.0'
#  project 'TangramKit.xcodeproj'
#  pods
#end

post_install do |installer|
    installer.generated_projects.each do |project|
        project.targets.each do |target|
            target.build_configurations.each do |config|
                config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'
                config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '12.0'
                config.build_settings['ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES'] = 'NO'
                config.build_settings["EXCLUDED_ARCHS[sdk=iphonesimulator*]"] = "arm64"
                config.build_settings['ENABLE_BITCODE'] = 'NO'
                config.build_settings['CODE_SIGN_IDENTITY'] = ''
                if config.name == 'Debug'
                    config.build_settings['STRIP_INSTALLED_PRODUCT'] = 'NO'
                else
                    config.build_settings['STRIP_INSTALLED_PRODUCT'] = 'YES'
                end
            end
        end
    end
end
