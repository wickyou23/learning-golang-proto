PROTOC_GEN_DIR=gen
PROTOC_INC_AUTH_DIR=auth-service
PROTOC_INC_CHAT_DIR=chat-service

AUTH_PROTO_FILES=$(wildcard $(PROTOC_INC_AUTH_DIR)/*.proto)
CHAT_PROTO_FILES=$(wildcard $(PROTOC_INC_CHAT_DIR)/*.proto)

all: gen_auth gen_chat

gen_auth: $(AUTH_PROTO_FILES)
	@mkdir -p $(PROTOC_GEN_DIR)
	protoc -I=$(PROTOC_INC_AUTH_DIR) --experimental_allow_proto3_optional --go_out=$(PROTOC_GEN_DIR) $^

gen_chat: $(CHAT_PROTO_FILES)
	@mkdir -p $(PROTOC_GEN_DIR)
	protoc -I=$(PROTOC_INC_CHAT_DIR) --experimental_allow_proto3_optional --go_out=$(PROTOC_GEN_DIR) $^

clean:
	rm -rf $(PROTOC_GEN_DIR)

.PHONY: all gen_auth gen_chat clean
