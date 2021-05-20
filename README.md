# logstash-elasticsearch-api-data

Trying to convert a string field value into float. The converted value has to be in new new field.
See code in logstash-config/convert-string-to-float.conf


<h2>Calculating difference in two datetime fields - logstash - ruby </h2>
Input file has two dates - A-date and B-date
see file input-data/date-sample.json

[Logstah config file](https://github.com/superriya/logstash-elasticsearch-api-data/blob/main/logstash-config/json_file.conf) with ruby filter to calculate time difference
see file output-logstash/date-sample-output.json (output of logstash)

I'm trying to explain the code below:
First we include 'time' library of ruby in our logstash using line ``` init => "require 'time'"  ```
Lets convert our datetime fields into iso format (unix format) by line ``` to_date_v   = Time.iso8601(event.get("[B-date]").to_s).to_i ```
- event.get("[B-date]") - captures value of a field B-date
- Time.iso8601().to_s - function convert datetime to iso format or also known as unix date format & converts it into seconds
- to_i - convert value to integer
At last we are assigning these values to fields, so we get them in logstash output

<h3>Proud to say - This is solution to How to calculate timediff of two fields in the same event
</h3>
https://discuss.elastic.co/t/logstash-ruby-filter-to-subtract-difference-between-two-timestamps-in-single-event/32580/4
https://discuss.elastic.co/t/how-to-calculate-timediff-of-two-fields-in-the-same-event/106417

Thanks :)
