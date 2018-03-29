# Chef to Docker

> Example of running chef-client in a Docker container

## Chef-apply

```
docker build \
	--tag chefnode \
	.
docker run \
	-v "$(pwd)"/sayhello.rb:/sayhello.rb \
	chefnode \
	chef-apply sayhello.rb
```

## Hello world commands

```
cat <<'EOL' | chef-apply --stdin 
execute 'sayhello' do
  command 'echo "hello world!"'
  live_stream true
end
EOL

cat <<'EOL' | chef-apply --stdin 
file 'hello.txt' do
  content 'Welcome to Chef'
end
EOL
```