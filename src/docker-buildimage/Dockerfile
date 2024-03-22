FROM mcr.microsoft.com/dotnet/sdk:8.0
LABEL author="cschroeder"
COPY ["nupkg", "nupkg"]
RUN apt-get update && \
	dotnet tool install --add-source ./nupkg  -g GitVersion.ToolIvu && \
	curl -L https://github.com/OctopusDeploy/cli/raw/main/scripts/install.sh | bash && \
	apt-get install -y apt-transport-https ca-certificates curl gnupg && \
	install -m 0755 -d /etc/apt/keyrings && \
	curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
	chmod a+r /etc/apt/keyrings/docker.gpg && \
	echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null && \
	apt-get update && \
	apt-get -y install docker-ce-cli
ENV PATH="$PATH:/root/.dotnet/tools" \
DOTNET_ROLL_FORWARD=Major \
TZ=Europe/Berlin \
LANG=de_DE.UTF-8 \
LANGUAGE=${LANG} \
LC_ALL=${LANG}