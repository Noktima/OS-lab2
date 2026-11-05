FROM gcc:13 AS build

WORKDIR /src
COPY . .

RUN make -C lib

RUN make -C apps/backend

FROM debian:bookworm-slim

WORKDIR /app

COPY --from=build /src/apps/backend/backend ./backend

EXPOSE 9000
ENTRYPOINT ["./backend"]
