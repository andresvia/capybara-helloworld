require 'capybara'
require 'capybara/dsl'
require 'capybara/poltergeist'
Capybara.run_server = false
Capybara.app_host = 'http://www.google.com.co/'
include Capybara::DSL
Capybara.register_driver :poltergeist do |app|
  Capybara::Poltergeist::Driver.new(app, :js_errors => false)
end
Capybara.current_driver = :poltergeist
def search!
  visit('/')
  within('body') do
    fill_in 'q', :with => 'cute cat'
  end
  click_button 'Buscar con Google'
  page.save_screenshot('screenshot.png')
end
desc 'do a test'
task :test do
  search!
end
