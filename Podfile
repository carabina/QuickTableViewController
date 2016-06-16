platform :ios, "8.0"
use_frameworks!

workspace "QuickTableViewController"

target "Example" do
  project "Example/Example"
  pod "QuickTableViewController", path: "./"
end

target "QuickTableViewControllerTests-iOS" do
  project "QuickTableViewController"
  pod "Quick"
  pod "Nimble"
end


# Specify Swift version in the configs for all the pods installed.
post_install do |installer|
  installer.pods_project.targets.each do |target|
    next if target.name.start_with? "Pods-"

    config = "#{Dir.pwd}/Pods/Target Support Files/#{target.name}/#{target.name}.xcconfig"
    if not File.exists? config
      puts "Missing #{config}"
      next
    end

    puts "Adding SWIFT_VERSION=2.3 to #{config}"
    File.open(config, "a") { |file| file << "SWIFT_VERSION=2.3\n" }
    puts "Done"
  end
end
