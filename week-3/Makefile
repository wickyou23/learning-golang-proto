# Directories for generated code and proto files
PROTOC_GEN_DIR=gen
PROTOC_INC_AUTH_DIR=auth-service
PROTOC_INC_CHAT_DIR=chat-service

# Wildcard pattern to find proto files in auth-service and chat-service directories
AUTH_PROTO_FILES=$(wildcard $(PROTOC_INC_AUTH_DIR)/*.proto)
CHAT_PROTO_FILES=$(wildcard $(PROTOC_INC_CHAT_DIR)/*.proto)

# Target to generate both auth and chat files
all: gen_auth gen_chat

# Generate code for auth-service .proto files
gen_auth: $(AUTH_PROTO_FILES)
	@mkdir -p $(PROTOC_GEN_DIR)/auth-service
	protoc -I=$(PROTOC_INC_AUTH_DIR) --experimental_allow_proto3_optional \
		--go_out=$(PROTOC_GEN_DIR)/auth-service --go-grpc_out=$(PROTOC_GEN_DIR)/auth-service \
		--go_opt=paths=source_relative --go-grpc_opt=paths=source_relative $^

# Generate code for chat-service .proto files
gen_chat: $(CHAT_PROTO_FILES)
	@mkdir -p $(PROTOC_GEN_DIR)/chat-service
	protoc -I=$(PROTOC_INC_CHAT_DIR) --experimental_allow_proto3_optional \
		--go_out=$(PROTOC_GEN_DIR)/chat-service --go-grpc_out=$(PROTOC_GEN_DIR)/chat-service \
		--go_opt=paths=source_relative --go-grpc_opt=paths=source_relative $^

# Clean the generated code directory
clean:
	rm -rf $(PROTOC_GEN_DIR)

.PHONY: all gen_auth gen_chat clean