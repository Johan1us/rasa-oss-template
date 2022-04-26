# Create a layer of the specified Docker image.
FROM rasa/rasa:3.0.0

# Add files from your current directory.
COPY config.yml /app/

# Get root access to the images resources.
USER root

# Set up the locale and change the local varibles
RUN apt-get clean
RUN apt-get update
RUN apt-get install -y locales locales-all
RUN locale-gen nl_NL.UTF-8
ENV LANG nl_NL.UTF-8
ENV LANGUAGE nl_NL:nl
ENV LC_ALL nl_NL.UTF-8

# Modify the pip packages
RUN pip install --no-cache-dir --upgrade pip
RUN pip install --no-cache-dir spacy==3.2.4
RUN python3 -m spacy download nl_core_news_md

# Run these commands -> source ?
USER 1001
CMD ["start", "--actions", "actions"]
