# =================
FROM python:3.8-alpine as base
# =================

WORKDIR /usr/pymetangine

RUN apk update && apk add make g++ build-base cmake && \
    python3 -m pip install pip==23.0

COPY ./build/requirements.txt .
RUN python3 -m pip install -r requirements.txt

# =================
FROM docker.io/attilamester/r2-5.8.8 as main
# =================

WORKDIR /usr/pymetangine

COPY --from=base /usr/local/bin/python3.8 /usr/local/bin/python3.8
COPY --from=base /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages
COPY --from=base /usr/local/lib/* /usr/local/lib
COPY --from=base /usr/lib/* /usr/lib
COPY --from=base /usr/include/* /usr/include
COPY --from=base /usr/share/* /usr/share

COPY *ngine.py ./

ENTRYPOINT ["python3", "-m", "pymetangine"]