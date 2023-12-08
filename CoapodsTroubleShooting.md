
# CocoapodTroubleshooting

When running $ sudo gem install cocoapods, you might run into this error for m1 processors:
"You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory."
(you will need to have hombrew installed for this solution)

1. You will need to install rvm to be able to change the version of ruby your are using.
$ \curl -sSL https://get.rvm.io | bash

2. Reopen Terminal and run(in my case ruby 3.2.0 is the one that worked you might have to use another version in the future)  
$ rvm install ruby-3.2.0 

3. Update your PATH by running this command
$ echo 'export PATH="/opt/hombrew/opt/ruby/bin:/usr/local/lib/ruby/gems/3.2.0/bin:$PATH"' >> ~/.zshrc

4. Set your new version of as your default.
$ rvm --default use 3.2.0

5. Check that you're now using the non-system version ruby.
$ which ruby 
It should not be /usr/bin/ruby

6. Try installing cocoapods again
$ sudo gem install cocoapods

7. If this gives you an error: "Error running '__rvm_make -j12',
please read /Users/h_iqbal/.rvm/log/1691057288_ruby/make.log" you will have to reinstall rvm 
$ rvm reinstall 3.2.0 --with-openssl-dir=$(brew --prefix openssl) --with-readline-dir=$(brew --prefix readline) --with-libyaml-dir=$(brew --prefix libyaml) --disable-dtrace --disable-docs

8. Repeat steps 4 and 6



