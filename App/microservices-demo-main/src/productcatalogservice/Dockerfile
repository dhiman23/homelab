FROM golang:1.25-alpine AS build
WORKDIR /app
COPY . .
RUN go mod download
RUN go build -o /go/app/productcatalogservice ./

FROM alpine AS release
WORKDIR /app
COPY --from=build /go/app/productcatalogservice ./
COPY products.json ./
EXPOSE 3550
CMD ["./productcatalogservice"]