# modmail-selfhosted

This is a fork of [chamburr/modmail](https://github.com/chamburr/modmail) that makes some adjustments to help with self-hosting.

 - Uses a custom build of [chamburr/twilight-dispatch](https://github.com/chamburr/twilight-dispatch/), [furrz/twilight-dispatch-selfhosted](https://github.com/furrz/twilight-dispatch-selfhosted), which removes a single dockerfile line that was forcing the project to build for a specific CPU architecture and caused problems when running in docker on M1.

 - Strips out the website from the docker-compose configuration, because running the website only makes sense for the original modmail dev's official instance.

 - Hosts new images for all of these in the GHCR, just to help with running these tweaked versions.

If trying to run on M1 mac, be sure to use this sequence - the hosted images do not seem to like cooperating on M1:

```bash
git submodule init --recursive
git submodule update
docker compose build
```

# ModMail

[![Discord](https://discord.com/api/guilds/576016832956334080/widget.png)][discord]
[![License](https://img.shields.io/github/license/chamburr/modmail.svg)](LICENSE)

A feature-rich Discord bot for easy communication between server staff and users.

![Screenshot](https://user-images.githubusercontent.com/42373024/194307657-9a146d26-c5ac-4138-8428-a78d2cacf6a6.png)

A new channel is created whenever a user messages the bot, and the channel will serve as a shared
inbox for seamless communication between staff and the user.

To learn more, check out our [website](https://modmail.xyz) or visit our [Discord server][discord].

## Contributing

There are many ways you can contribute to this project:

- [Submitting bugs and suggestions](https://github.com/chamburr/modmail/issues)
- [Reviewing pull requests](https://github.com/chamburr/modmail/pulls)
- [Contribute directly to the code base](https://github.com/chamburr/modmail/pulls)

For more information, please see our [contributing guidelines](CONTRIBUTING.md).

The issue tracker here is only for bug reports and suggestions. Please do not use it to ask a
question. Instead, ask it on our [Discord server][discord].

## Self-hosting

This guide requires you to have basic knowledge about command line, Docker and Discord bots. We
will not provide any form of support for self-hosting.

First, create a Discord bot on the [developer portal](https://discord.com/developers). You must
enable the server member intent and the message content intent for the bot to function.

Then, install Git and Docker on your machine. Clone this repository, copy `docker/.env.example` to
`docker/.env` and fill in all the empty configurations.

Finally, use the following commands to start ModMail.

```
cd docker
docker compose up -d
```

If you prefer to build your own images for local development, then use these commands.

```
cd docker
docker compose build
docker compose up -d
```

Your self-hosted bot should be up now. Congratulations!

## License

This project is licensed under [GNU Affero General Public License v3.0](LICENSE).

[discord]: https://discord.gg/wjWJwJB
