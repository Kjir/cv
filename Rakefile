task default: %w[markdown pdf]

task :pdf do
  sh "json_resume convert --out=pdf sb_cv.yaml"
  sh "mv resume.pdf cv.pdf"
end

task md: %w[markdown]
task :markdown do
  sh "json_resume convert --out=md sb_cv.yaml"
  sh "mv resume.md README.md"
end
