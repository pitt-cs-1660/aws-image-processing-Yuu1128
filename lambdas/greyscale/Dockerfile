FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY pyproject.toml ./
RUN uv pip install --system --no-cache -e .

COPY handler.py ${LAMBDA_TASK_ROOT}

CMD ["handler.greyscale_handler"]
