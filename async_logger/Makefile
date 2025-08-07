export GOBIN

.PHONY: install gen test check-env

install:
	go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27.1
	go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0

gen:
	protoc --version
	protoc-gen-go --version
	protoc-gen-go-grpc --version
	protoc --go_out=. --go-grpc_out=. service.proto
	sed -i 's/package __/package main/g' *.pb.go

test:
	go test -v -race

check-env:
ifneq ($(GOBIN),)
	@echo "✅ GOBIN is set to: $(GOBIN)"
else
	$(error GOBIN is undefined, set GOBIN so protoc can see installed plugins in PATH)
endif