require "bundler/gem_tasks"
require "rake/testtask"
require "rake/extensiontask"

task default: :test
Rake::TestTask.new do |t|
  t.libs << "test"
  t.pattern = "test/**/*_test.rb"
  t.warning = false
end

Rake::ExtensionTask.new("youtokentome") do |ext|
  ext.name = "ext"
  ext.lib_dir = "lib/youtokentome"
end

# include ext in local installs but not releases
task :remove_ext do
  path = "lib/youtokentome/ext.bundle"
  File.unlink(path) if File.exist?(path)
end

Rake::Task["release:guard_clean"].enhance [:remove_ext]
