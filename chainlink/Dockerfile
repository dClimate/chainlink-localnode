# Get the latest node image
FROM smartcontract/chainlink:0.10.3

# Run our own entry point to initialise the node
COPY .api /.api
RUN chmod +x /.api
COPY .password /.password
RUN chmod +x /.password
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT /entrypoint.sh