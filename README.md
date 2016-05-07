# Watchiot SDK for Ruby

If you want to create an monitor agent in **Ruby** we suggest use this **gem**, it contains easy way to interact with our api.

## Install

```bash
$ gem install wiot_sdk
```

## Usage

First you need to add the dependence in your project *Gemfile*

```ruby
gem 'wiot_sdk', '~> 0.1'
```

Then you have to require the sdk where are you going to use it

```ruby
require 'wiot_sdk'
```

or

```ruby
require 'wiot-sdk'
```
it work too

Now you have to set mandatory configuration variables that always will be send in each request. This parameters are:
**api key**, **name space** and **name project**
 
```ruby
def init_sdk
  my_api_key = 'asd123asd-23asd-123sda-1231234saa'
  my_namespace = 'my_space'
  my_project = 'my_project'
  
  client = WiotSdk.init my_api_key, my_namespace, my_project
end
```

the other way is put the yml or json file path where this parameters are setting 

```ruby
def init_sdk
  my_config_json = '/home/myhome/my_agent/my_agent.json'
 
  client = WiotSdk.init my_config_json
end
```

```ruby
def init_sdk
  my_config_yml = '/home/myhome/my_agent/my_agent.yml'
  
  client = WiotSdk.init my_configyml
end
```
Example of config file

* json
```json
{
  api_key: "asd123asd-23asd-123sda-1231234saa",
  space  : "my_space",
  project: "my_project"
}
```

* yml
```yml
api_key: "asd123asd-23asd-123sda-1231234saa"
space  : "my_space"
project: "my_project"
```

Now you are ready to send us a request with the metrics that you recollect.

To fill the **metric** us provide you a *Metric class*

```ruby
require 'wiot_sdk/metric'

def fill_metric
 metric = Metric.new
 
 metric.add('my_param1', 'my_malue1')
 metric.add('my_param2', 'my_malue2')
 metric.add('my_param3', 'my_malue3')
 ...
 metric.add('my_paramN', 'my_malueN')
end
```
Whe you have the metric only you need send a request to us

```ruby

def request
 client = init_sdk
 metric = fill_metric
 
 response = client.send metric
rescue => ex
 # 404, 401, etc
end
```

## License

(The MIT License)

Copyright (c) 2016 WatchIoT

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

