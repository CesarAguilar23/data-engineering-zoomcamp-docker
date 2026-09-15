FROM python:3.13.11-slim

#RUN pip install pandas pyarrow
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin

WORKDIR /code
# With this we establish the virtual environment.
# We don have to do uv run now. 
ENV PATH="/code/.venv/bin:$PATH"

# Copy dependency files first
COPY pyproject.toml .python-version uv.lock ./

# Install dependencies from lock file

#RUN uv sync --locked
# Change so uv doesnt try to install pipeline.py.
RUN uv sync --locked --no-install-project
# Copy pipeline coe 
COPY pipeline.py .

ENTRYPOINT ["python","pipeline.py"]

#ENTRYPOINT ["uv","run","python","pipeline.py"]