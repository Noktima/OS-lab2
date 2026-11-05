FROM gcc:13 as build

WORKDIR /src
COPY . .

RUN make -C lib
RUN make -C apps/loadgen

FROM debian:bookworm-slim

WORKDIR /app
COPY --from=build /src/apps/loadgen/loadgen ./loadgen


ENTRYPOINT ["./loadgen"]
