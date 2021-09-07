# Start from the alpine image that is smaller but no fancy tools
FROM alpine:3.13
# Use /usr/src/app as our workdir. The following instructions will be executed in this location.
WORKDIR /usr/src/app

# Copy the hello.sh file from this location to /usr/src/app/ creating /usr/src/app/output.sh
COPY output.sh .

# Alternatively, if we skipped chmod earlier, we can add execution permissions during the build.
RUN chmod +x output.sh

# When running docker run the command will be ./output.sh
CMD ./output.sh