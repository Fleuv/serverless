# Serverless

[![dockeri.co](https://dockeri.co/image/fleuv/serverless)](https://hub.docker.com/r/fleuv/serverless)

A simple docker container which can be used to run [serverless](https://www.serverless.com/) commands.

## Usage

1. Create a new file in one of your `$PATH` directories and name it e.g. `wrangler`. For linux I suggest using the following command:

   ```
   touch /usr/local/bin/serverless
   ```

2. Add executable permission to the file, in linux it's done like this:

   ```
   chmod +x /usr/local/bin/serverless
   ```

3. Use your favorite editor to add the following contents to the file (only tested in linux):

   ```
   #!/bin/sh

   docker run \
       --rm \
       -v "$PWD":/app \
       --name usr-local-bin-serverless \
       fleuv/serverless:latest \
       "$@"

   exit $?
   ```

4. Use `serverless` from a CLI in a local project its root directory.

### Extra

- Add a symbolic link to executable to alias the `serverless` e.g. as `sls`, on linux you could do something like this:
  ```
  ln -s /usr/local/bin/serverless /usr/local/bin/sls
  ```

## License

MIT
