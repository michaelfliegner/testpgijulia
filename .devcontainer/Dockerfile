FROM postgres
ARG JULIA_URL="https://julialang-s3.julialang.org/bin/linux/x64/1.10/julia-1.10.3-linux-x86_64.tar.gz" 
ARG JULIA_MINOR_VERSION="1.10"
ARG JULIA_BUGFIX_VERSION="1.10.3"

RUN apt-get update && apt-get install -y direnv \
  && direnv hook bash >> ~/.bashrc \
  && echo "export PATH=~/julia/bin:$PATH" >> ~/.bashrc
RUN apt-get install -y curl
RUN curl -L "${JULIA_URL}" | tar -xzf - \
  && mv julia-${JULIA_BUGFIX_VERSION} julia 
RUN export PATH=~/julia/bin:$PATH \
  && julia -e "using Pkg; Pkg.add(\"IJulia\")"
