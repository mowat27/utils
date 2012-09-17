# Global rake file

class ::String
  def cleanse
    result = self.clone
    result.gsub!(/\t/, "  ")
    result.gsub!(/ +$/, "")
    result
  end
end

namespace :ruby do
  task :tidy_all do |t|
    if !File.file?("./Rakefile") 
      STDERR.puts "ERROR : #{Dir.getwd} must be a ruby project with a Rakefile"
      exit(1)
    end

    puts "Formatting all ruby files under #{Dir.getwd}"
    puts "Files changed..."
    
    files = Dir['**/*.rb']
    files.each do |path|
      original_text = File.read(path)
      new_text = original_text.cleanse
      
      if original_text != new_text
        puts "  #{path}" 
        File.open(path, "w") {|f| f.puts new_text}
      end
    end
  end
end
