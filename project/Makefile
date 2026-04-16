.PHONY: check pull

IMAGES := \
	python:3.14.3-slim \
	dhi.io/python:3.14-alpine3.23-fips-dev \
	dhi.io/node:25 \
	dhi.io/node:25-dev \
	node:25 \
	node:20 \
	node:20-alpine \
	node:22 \
	node:22-alpine \
	debian:bookworm-slim

check:
	@echo "Checking required tools...\n"
	@check() { \
		if command -v "$$1" > /dev/null 2>&1; then \
			printf "  %-20s %s\n" "$$1" "OK  ($$($$1 $$2 2>&1 | head -1))"; \
		else \
			printf "  %-20s %s\n" "$$1" "MISSING"; \
			FAILED=1; \
		fi; \
	}; \
	check docker "--version"; \
	check jq "--version"; \
	check vexctl "version"; \
	check oras "version"; \
	check trivy "--version"; \
	check cosign "version"; \
	if docker buildx version > /dev/null 2>&1; then \
		printf "  %-20s %s\n" "docker buildx" "OK  ($$(docker buildx version 2>&1 | head -1))"; \
	else \
		printf "  %-20s %s\n" "docker buildx" "MISSING"; \
		FAILED=1; \
	fi; \
	if docker scout version > /dev/null 2>&1; then \
		printf "  %-20s %s\n" "docker scout" "OK  ($$(docker scout version 2>&1 | head -1))"; \
	else \
		printf "  %-20s %s\n" "docker scout" "MISSING"; \
		FAILED=1; \
	fi; \
	if docker sbom --version > /dev/null 2>&1; then \
		printf "  %-20s %s\n" "docker sbom" "OK  ($$(docker sbom --version 2>&1 | head -1))"; \
	else \
		printf "  %-20s %s\n" "docker sbom" "MISSING"; \
		FAILED=1; \
	fi; \
	echo ""; \
	if [ "$${FAILED}" = "1" ]; then \
		echo "Some tools are missing. See installation.md for instructions."; \
		exit 1; \
	else \
		echo "All tools are installed."; \
	fi

pull:
	@echo "Pulling required images...\n"
	@for image in $(IMAGES); do \
		echo "  Pulling $$image..."; \
		docker pull $$image; \
	done
	@echo "\nAll images pulled."
