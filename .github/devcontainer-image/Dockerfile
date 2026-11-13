FROM mcr.microsoft.com/devcontainers/java:25-trixie@sha256:ba69d01f9f399529047736a1fe541ea1c7e783be726c362be2b91d4e125d928a
# Mount points for named volumes, owned by vscode: a new, empty named volume copies the ownership of the image
# directory it's mounted on, so no runtime chown is needed.
RUN install -d -o vscode -g vscode /home/vscode/.config /home/vscode/.config/gh \
      /home/vscode/.gradle /home/vscode/.local /home/vscode/.local/scratch
