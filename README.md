# rspec + JRuby 9k on Tobi's machine = :'(

A minimal test repo to demonstrate issues experienced with rspec and jruby 9k.

## Steps to reproduce

    bundle exec rspec

Result on 9k:

    tobi@airship ~/github/rspec-vs-jruby-9k $ ruby -v
    jruby 9.0.0.0 (2.2.2) 2015-07-21 e10ec96 OpenJDK 64-Bit Server VM 24.79-b02 on 1.7.0_79-b14 +jit [linux-amd64]
    tobi@airship ~/github/rspec-vs-jruby-9k $ bundle exec rspec
    uri:classloader:/jruby/kernel/kernel.rb:28: warning: unsupported exec option: close_others
    LoadError: no such file to load -- spec/spec_helper
              require at org/jruby/RubyKernel.java:940
                <top> at /home/tobi/github/rspec-vs-jruby-9k/spec/example/example_spec.rb:1
                 load at org/jruby/RubyKernel.java:958
      block in (root) at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/configuration.rb:1
                 each at org/jruby/RubyArray.java:1560
      load_spec_files at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/configuration.rb:1226
      load_spec_files at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/configuration.rb:1224
                setup at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/runner.rb:97
                  run at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/runner.rb:85
                  run at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/runner.rb:70
                <top> at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/lib/rspec/core/runner.rb:38
                 load at org/jruby/RubyKernel.java:958
               <eval> at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/gems/rspec-core-3.2.3/exe/rspec:4
                 eval at org/jruby/RubyKernel.java:979
                <top> at /home/tobi/.rvm/gems/jruby-9.0.0.0@rspec-9k/bin/jruby_executable_hooks:15

Works fine on 1.7.21:

    tobi@airship ~/github/rspec-vs-jruby-9k $ ruby -v
    jruby 1.7.21 (1.9.3p551) 2015-07-07 a741a82 on OpenJDK 64-Bit Server VM 1.7.0_79-b14 +jit [linux-amd64]
    tobi@airship ~/github/rspec-vs-jruby-9k $ rspec
    .
    
    Finished in 0.008 seconds (files took 0.646 seconds to load)
    1 example, 0 failures
    
    tobi@airship ~/github/rspec-vs-jruby-9k $ 
