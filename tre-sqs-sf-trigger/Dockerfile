FROM public.ecr.aws/lambda/python:3.13
ARG PIP_INDEX_URL

# Copy function code
COPY tre_sqs_sf_trigger.py ${LAMBDA_TASK_ROOT}

# Install the function's dependencies using file requirements.txt
COPY requirements.txt ./requirements.txt
RUN dnf clean all --enablerepo=\* \
    && pip3 install --no-cache-dir --requirement requirements.txt --target "${LAMBDA_TASK_ROOT}"

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "tre_sqs_sf_trigger.handler" ]
