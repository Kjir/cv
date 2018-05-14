require 'fileutils'

task default: %w(markdown pdf tech tech_pdf)

desc "Generate PDF version of CV"
task pdf: %w(stephane_bisinger_cv.pdf)
file 'stephane_bisinger_cv.pdf' => 'sb_cv.yaml' do
  sh 'json_resume convert --out=html_pdf --template=templates/default_html.mustache sb_cv.yaml'
  FileUtils.mv 'resume.pdf', 'stephane_bisinger_cv.pdf'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'stephane_bisinger_cv.pdf', "versions/#{@current_date}_cv.pdf"
end

desc "Generate Markdown version of CV"
task md: %w(markdown)
task markdown: %w(README.md)
file 'README.md' => 'sb_cv.yaml' do
  sh 'json_resume convert --out=md --template=templates/default_md.mustache sb_cv.yaml'
  FileUtils.mv 'resume.md', 'cv.md'
  FileUtils.cp 'cv.md', 'README.md'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'cv.md', "versions/#{@current_date}_cv.md"
end

desc "Generate PDF version of Technology CV"
task tech_pdf: %w(technology_cv.pdf)
file 'technology_cv.pdf' => 'technology_cv.yaml' do
  sh 'json_resume convert --out=html_pdf technology_cv.yaml'
  FileUtils.mv 'resume.pdf', 'technology_cv.pdf'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'technology_cv.pdf', "versions/#{@current_date}_technology_cv.pdf"
end

desc "Generate HTML version of Technology CV"
task tech_html: %w(technology.html)
file 'technology.html' => 'technology_cv.yaml' do
  sh 'json_resume convert technology_cv.yaml'
  @current_date = Time.now.strftime("%F")
end

desc "Generate Markdown version of Technology CV"
task tech: %w(tech_md)
task tech_md: %w(technology.md)
file 'technology.md' => 'technology_cv.yaml' do
  sh 'json_resume convert --out=md technology_cv.yaml'
  FileUtils.mv 'resume.md', 'technology.md'
  @current_date = Time.now.strftime("%F")
  FileUtils.cp 'technology.md', "versions/#{@current_date}_technology.md"
end

task :test do
  @current_date = Time.now.strftime("%F")
  puts "#{@current_date}"
end
