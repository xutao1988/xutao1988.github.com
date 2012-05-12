# coding: utf-8
require "rubygems"
require "bundler/setup"
require 'rake'
require 'fileutils

task :default => [:start]



task :runwindows do
    puts '* Changing the codepage'
    `chcp 65001`
    puts ('* Running Jekyll')
    `jekyll --server --auto`
end

desc "Startup Jekyll"
task :start do
  sh "jekyll --server"
end


