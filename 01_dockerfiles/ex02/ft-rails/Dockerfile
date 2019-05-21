#build image: docker build . -t ft-rails:on-build 
FROM ruby

RUN apt-get -y update && apt-get -y upgrade 
ENV PATH=/usr/local/rvm/gems/ruby-2.6.3/bin:/usr/local/rvm/gems/ruby-2.6.3@global/bin:/usr/local/rvm/rubies/ruby-2.6.3/bin:/usr/local/rvm/bin::$PATH
ENV GEM_PATH=/usr/local/rvm/gems/ruby-2.6.3:/usr/local/rvm/gems/ruby-2.6.3@global
ENV MY_RUBY_HOME=/usr/local/rvm/rubies/ruby-2.6.3
ENV rvm_bin_path=/usr/local/rvm/bin
ENV GEM_HOME=/usr/local/rvm/gems/ruby-2.6.3
#RUN /bin/bash -l -c "echo \"PATH=\$PATH\" >> /etc/profile"
RUN /bin/bash -c "gem install bundler"
RUN /bin/bash -c "gem install rake"
RUN /bin/bash -c "gem install rails"
RUN mkdir -p /opt/app
WORKDIR /opt/app 

ONBUILD ADD ./project  /opt/app
ONBUILD RUN /bin/bash -c "bundle install"
ONBUILD RUN /bin/bash -c "bundle update"
ONBUILD RUN /bin/bash -c "rake db:migrate"
ONBUILD RUN /bin/bash -c "rake db:seed"
 
#CMD ["bash"]
