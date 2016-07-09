require 'fileutils'

task default: %w(markdown pdf)

desc "Generate PDF version of CV"
task pdf: %w(cv.pdf)
file 'cv.pdf' => 'sb_cv.yaml' do
  sh 'json_resume convert --out=pdf sb_cv.yaml'
  FileUtils.mv 'resume.pdf', 'cv.pdf'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'cv.pdf', "versions/#{@current_date}_cv.pdf"
end

desc "Generate PDF version of CV"
task md: %w(markdown)
task markdown: %w(README.md)
file 'README.md' => 'sb_cv.yaml' do
  sh 'json_resume convert --out=md sb_cv.yaml'
  FileUtils.mv 'resume.md', 'cv.md'
  FileUtils.cp 'cv.md', 'README.md'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'cv.md', "versions/#{@current_date}_cv.md"
end

task :test do
  @current_date = Time.now.strftime("%F")
  puts "#{@current_date}"
end
