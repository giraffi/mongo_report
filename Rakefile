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

  report << `mongo #{db} --quiet --eval 'configDB = db.getSisterDB("config");configDB.collections.find({_id:new RegExp("^" + "#{db}" + "\\.")}).sort({_id:1}).forEach(function (coll) {print( coll._id + " chunks:");res = configDB.chunks.group({cond:{ns:coll._id}, key:{shard:1}, reduce:function (doc, out) {out.nChunks++;}, initial:{nChunks:0}});var totalChunks = 0;res.forEach(function (z) {totalChunks += z.nChunks;print("\t" + z.shard + "\t" + z.nChunks);})})'`
  puts report

end


desc "Sharding chanks report"
task "chanks" do

  db = ENV["db_name"] || "local"

  report =<<EOL
----------------------------------------------------
#{db} chanks count.
----------------------------------------------------
EOL

  report<< `mongo #{db} --quiet --eval 'configDB = db.getSisterDB("config");configDB.collections.find({_id:new RegExp("^" + "#{db}" + "\\.")}).sort({_id:1}).forEach(function (coll) {print( coll._id + " chunks:");res = configDB.chunks.group({cond:{ns:coll._id}, key:{shard:1}, reduce:function (doc, out) {out.nChunks++;}, initial:{nChunks:0}});var totalChunks = 0;res.forEach(function (z) {totalChunks += z.nChunks;print("\t" + z.shard + "\t" + z.nChunks);})})'`

  report<< <<EOL


EOL

  puts report

end
