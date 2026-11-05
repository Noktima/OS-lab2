FROM gcc:13 as build

WORKDIR src/
COPY . .

RUN make -C lib
RUN make -C apps/balancer

FROM debian:bookworm-slim

WORKDIR app/
COPY --from=build /src/apps/balancer/balancer ./balancer

EXPOSE 8080
ENTRYPOINT ["./balancer"]
