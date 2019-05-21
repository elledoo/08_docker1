#to create image: docker build . -t parent
#to run container: docker run -it -p 3000:3000 parent
FROM ft-rails:on-build
EXPOSE 3000
#ENTRYPOINT ["sh"]
CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]
