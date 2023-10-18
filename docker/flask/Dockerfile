FROM ubuntu:20.04
WORKDIR /app
RUN apt-get update -y 
RUN apt-get install -y curl unzip gnupg xvfb libxi6 libgconf-2-4 default-jdk wget software-properties-common
#chromium-browser from https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+build/25972322
COPY chromium-codecs-ffmpeg_112.0.5615.49-0ubuntu0.18.04.1_arm64.deb /tmp/
COPY chromium-browser_112.0.5615.49-0ubuntu0.18.04.1_arm64.deb /tmp/
#chromedriver from https://github.com/electron/electron/releases?q=112&expanded=true
COPY chromedriver /tmp/
RUN apt-get install -y libcairo2 libgbm1 libpango-1.0-0 libxdamage1 libxkbcommon0 xdg-utils
RUN dpkg -i /tmp/chromium-codecs-ffmpeg_112.0.5615.49-0ubuntu0.18.04.1_arm64.deb
RUN dpkg -i /tmp/chromium-browser_112.0.5615.49-0ubuntu0.18.04.1_arm64.deb
RUN apt-get install -y python3-pip python3-dev build-essential libcurl4-openssl-dev libssl-dev git
RUN apt-get install -y net-tools
RUN apt-get install -y procps
RUN pip3 install pycurl pymysql flask requests selenium
RUN pip3 install git+https://github.com/SergeyPirogov/webdriver_manager
RUN pip3 install regex

ENV admin_password [redacted]

ENV xss1_flag flag{this_is_xss1_flag}
ENV xss2_flag flag{this_is_xss2_flag}
ENV xss3_flag flag{this_is_xss3_flag}
ENV csrf1_flag flag{this_is_csrf1_flag}
ENV csrf2_flag flag{this_is_csrf2_flag}
ENV xsleak_flag flag{this_is_xsleak_flag}

RUN chmod +x /tmp/chromedriver
ENTRYPOINT /app/entrypoint.sh && /bin/bash
CMD ["true"]
