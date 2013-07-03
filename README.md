ruby_todo
=========

#
# convert string to boolean like true => 1, false => 0
# TODO, may need later
def to_bool
  return true if self == true || self =~ (/(true|t|yes|y|1)$/i)
  return false if self == false || self.blank? || self =~ (/(false|f|no|n|0)$/i)
  raise ArgumentError.new("invalid value for Boolean: \"#{self}\"")
end

#
# return, string camel case lower
#      
def camel_case_lower str
  str.split('_').inject([]){ |buffer,e| buffer.push(buffer.empty? ? e : e.capitalize) }.join
end

#
# return string camel case
#
def camel_case
  return self if self !~ /_/ && self =~ /[A-Z]+.*/
  split('_').map{|e| e.capitalize}.join
end

#
# camel case to underscore
#
def camel_case_to_underscore str
  str.gsub(/::/, '/').
  gsub(/([A-Z]+)([A-Z][a-z])/,'\1_\2').
  gsub(/([a-z\d])([A-Z])/,'\1_\2').
  tr("-", "_").downcase
end
