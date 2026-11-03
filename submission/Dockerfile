FROM public.ecr.aws/d3j8x8q7/olympus-base:latest

WORKDIR /app

COPY . .

# The tests run offline, so install pyserde with its supported formats and test
# dependencies during the image build. The package version normally comes from
# git tags, which a plain checkout may not carry.
ENV SETUPTOOLS_SCM_PRETEND_VERSION=0.34.0
RUN pip install --break-system-packages --retries 10 --timeout 60 \
      -e ".[msgpack,toml,yaml,numpy,jaxtyping]" \
      typing_extensions==4.15.0 casefy==1.1.0 jinja2==3.1.6 \
      plum-dispatch==2.6.0 beartype==0.22.6 \
      msgpack==1.1.2 tomli-w==1.2.0 PyYAML==6.0.3 \
      numpy==2.3.5 jaxtyping==0.3.9 \
      more-itertools==10.5.0 envclasses==0.3.1 jedi==0.19.2 \
      pytest==9.0.3 pytest-xdist==3.8.0

CMD ["/bin/bash"]
