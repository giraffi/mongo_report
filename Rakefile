# coding: utf-8
require "erb"
require "json"

desc "help"
task "default" do
  puts "hogehoge"
end


desc "Create mongodb report"
task "repo" do
  # initial
  db = ENV["db_name"] || "local"
  col = ENV["col_name"] || "collection"

  erb_tpl = File.read("./rp.erb")
  # col_stat = File.read("./sample.json")
  col_stat = `mongo #{db} --quiet --eval "printjson(db.#{col}.stats())"`

  @db_stat = JSON.parse(col_stat)
  report = ERB.new(erb_tpl, nil, "%").result

  puts report

end
