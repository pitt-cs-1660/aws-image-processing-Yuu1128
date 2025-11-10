FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# copy pyproject.toml and uv.lock, then install dependencies
COPY pyproject.toml uv.lock ${LAMBDA_TASK_ROOT}/
RUN uv sync --frozen --no-install-project

# copy the lambda handler
COPY handler.py ${LAMBDA_TASK_ROOT}/

# set Python path and command
ENV PYTHONPATH="${LAMBDA_TASK_ROOT}/.venv/lib/python3.13/site-packages:${LAMBDA_TASK_ROOT}"
CMD ["handler.greyscale_handler"]
