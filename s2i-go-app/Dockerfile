FROM s2i-do288-go
LABEL "io.k8s.display-name"="s2i-go-app" \
      "io.openshift.s2i.build.image"="s2i-do288-go" \
      "io.openshift.s2i.build.source-location"="/home/student/DO288/labs/custom-s2i/test/test-app"

USER root
# Copying in source code
COPY upload/src /tmp/src
# Change file ownership to the assemble user. Builder image must support chown command.
RUN chown -R 1001:0 /tmp/src
USER 1001
# Assemble script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
RUN /usr/libexec/s2i/assemble
# Run script sourced from builder image based on user input or image metadata.
# If this file does not exist in the image, the build will fail.
CMD /usr/libexec/s2i/run
