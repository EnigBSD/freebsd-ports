PORTNAME=	gojq
DISTVERSIONPREFIX=	v
DISTVERSION=	0.12.6
PORTREVISION=	1
CATEGORIES=	textproc

MAINTAINER=	nork@ninth-nine.com
COMMENT=	Pure Go implementation of jq

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules

GO_MODULE=	github.com/itchyny/gojq
GO_TARGET=	./cmd/gojq

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/share/zsh/site-functions
	${INSTALL_DATA} ${WRKSRC}/_gojq ${STAGEDIR}${PREFIX}/share/zsh/site-functions/

.include <bsd.port.mk>
