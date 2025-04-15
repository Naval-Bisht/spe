# Stage 1: Build the C application
FROM gcc:latest AS build

# Set working directory
WORKDIR /app

# Copy the C source code into the container
COPY hello.c .

# Compile the C program statically
RUN gcc -o hello hello.c -static

# Stage 2: Create a minimal runtime image
FROM alpine:latest

# Copy the compiled binary from the previous stage
COPY --from=build /app/hello /usr/local/bin/hello

# Ensure the binary has execute permissions
RUN chmod +x /usr/local/bin/hello

# Set the binary as the entry point
ENTRYPOINT ["hello"]

