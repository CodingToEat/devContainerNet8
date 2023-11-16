ARG VARIANT="7.0"
FROM mcr.microsoft.com/vscode/devcontainers/dotnet:0-${VARIANT}
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

RUN wget -O dotnet.tar.gz https://download.visualstudio.microsoft.com/download/pr/9144f37e-b370-41ee-a86f-2d2a69251652/bc1d544112ec134184a5aec7f7a1eaf9/dotnet-sdk-8.0.100-rc.2.23502.2-linux-x64.tar.gz \
    && dotnet_sha512='45f09e7b031f4cf5b4dcead240fe47e2e3731d97d22aa96d3a02a087322658606cc22792053c3784c44f15d7c9bad0ac9dbda90def7b4e197f2955dca9a5bb6c' \
    && echo "$dotnet_sha512 dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
    && rm dotnet.tar.gz

# [Optional] Uncomment this section to install additional OS packages.
#RUN apt-get update && \
#    export DEBIAN_FRONTEND=noninteractive && \
#    apt-get -qy full-upgrade && \
#    apt-get install -qy curl && \
#    apt-get -y install --no-install-recommends vim && \
#    curl -sSL https://get.docker.com/ | sh

# [Optional] Uncomment this section to add entity framework tools
#RUN dotnet tool install -g dotnet-ef
#ENV PATH $PATH:/root/.dotnet/tools