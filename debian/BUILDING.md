# Instructions assuming Ubuntu 24.04 build host on amd64 (WSL)

1.  Clone Nureva gRPC repo with the correct branch:

    `$ git clone https://github.com/nureva-com/grpc -b v1.59.3-nureva --depth=1 --recurse-submodules --shallow-submodules`
	
2.  Install necessary build dependencies:
	- Add arm64 as supported architecture:

	  `$ sudo dpkg --add-architecture arm64`

	  `$ sudo apt update`
	  
	- Install packages:

		`$ sudo apt install build-essential fakeroot dpkg-dev debhelper cmake libssl-dev pkg-config protobuf-compiler libsystemd-dev`

		`$ sudo apt install crossbuild-essential-arm64 libssl-dev:arm64 libsystemd-dev:arm64`

3.  Build amd64:

    `$ dpkg-buildpackage -us -uc -b` 

4. Build arm64:

	`$ dpkg-buildpackage -us -uc -b -aarm64`
	
	
Should produce .deb packages in .. for both amd64 and arm64, see instructions in grpc-ppa repo about how to sign etc.