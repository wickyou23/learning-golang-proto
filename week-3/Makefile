# Directories for generated code and proto files
PROTOC_GEN_DIR=gen
PROTOC_INC_AUTH_DIR=auth-service
PROTOC_INC_CHAT_DIR=chat-service

# Wildcard pattern to find proto files in auth-service and chat-service directories
AUTH_PROTO_FILES=$(wildcard $(PROTOC_INC_AUTH_DIR)/*.proto)
CHAT_PROTO_FILES=$(wildcard $(PROTOC_INC_CHAT_DIR)/*.proto)
PREFIX=github.com/wickyou23/learning-golang-proto/week-3/gen

# Target to generate both auth and chat files
all: gen_auth gen_chat

# Generate code for auth-service .proto files
gen_auth:
	@mkdir -p $(PROTOC_GEN_DIR)
	protoc -I=$(PROTOC_INC_AUTH_DIR) --experimental_allow_proto3_optional \
		--go_out=gen --go-grpc_out=gen \
		--go_opt=module=$(PREFIX) --go-grpc_opt=module=$(PREFIX) \
		$(AUTH_PROTO_FILES) $^

#Generate code for chat-service .proto files
gen_chat:
	@mkdir -p $(PROTOC_GEN_DIR)
	protoc -I=$(PROTOC_INC_CHAT_DIR) --experimental_allow_proto3_optional \
		--go_out=gen --go-grpc_out=gen \
		--go_opt=module=$(PREFIX) --go-grpc_opt=module=$(PREFIX) \
		$(CHAT_PROTO_FILES) $^

# Clean the generated code directory
clean:
	rm -rf $(PROTOC_GEN_DIR)

.PHONY: all gen_auth gen_chat clean