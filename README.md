# Steam Cleanplay Console

A web-based tool to check if players in a Team Fortress 2 or Counter-Strike: Global Offensive matches have any Steam bans. It also features a social graph to visualize the relationships between players based on their Steam friendships / relevant groups.

## Development

Vite is used for development and building the front-end application. It provides fast development with features like hot module replacement (HMR) and efficient production builds. Vite is configured using `vite.config.js` in the project root. All requests with the `/api` prefix are forwarded to the back-end Express server during development, using the vite server-proxy configuration

PRE: You need to have docker to run the image at /redis folder

- Rename .env.example to .env & update the values
- Run `npm run dev`

## Troubleshooting

- Read `redis/README.md`

## Deployment

- Replace "name" & "app" strings with your new app name at package.json at fly.toml (respectively)
- Run `npm i`
- Rename .env.example to .env
- Run `flyctl launch`
- When prompted for a builder, select builtin Nodejs.
- Run `npm run fly:deploy` (for future deployments only this command will be needed)

## Stopping / Starting app

- `npm run fly:stop`
- `npm run fly:start`

## Read app secrets

- `npm run fly:ssh`
- type `env`
- quit with `exit`

## Set app secrets

Add them to .env file. Alternatively use fly.io built command but note those take precedence over the ones at .env

- `flyctl secrets set SECRET="myvalue" -a <app-name>`

## Read server logs

From terminal

- `npm run fly:logs`

## Redis

Upstash Redis can be created with `flyctl redis create`

- `flyctl redis list` & copy redis name
- `flyctl redis status <redis-name>` & then copy the Private URL & set the proper env variable at the .env file

## Other

Currently hosted free of charge on Fly.io

- https://fly.io/blog/shipping-logs/
- https://fly.io/docs/reference/redis/
