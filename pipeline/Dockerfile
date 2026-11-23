
# Start with slim Python 3.13 image
FROM python:3.13.10-slim

# Copy uv binary from official uv image
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

# Set working directory
WORKDIR /app

# Add virtual environment to PATH
ENV PATH="/app/.venv/bin:$PATH"

# Copy dependency files first
COPY pyproject.toml uv.lock .python-version ./

# Install dependencies without installing the project
RUN uv sync --locked --no-install-project

# Copy application code
COPY ingest_data.py .

# Set entry point
ENTRYPOINT ["python", "ingest_data.py"]
