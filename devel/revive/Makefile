PORTNAME=	revive
DISTVERSIONPREFIX=	v
DISTVERSION=	1.2.0
CATEGORIES=	devel

MAINTAINER=	lcook@FreeBSD.org
COMMENT=	Extensible static code analysis framework for Go

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules

_BUILD_VERSION=	${DISTVERSION}
_BUILD_COMMIT=	671c55d
_BUILD_DATE=	$$(date +%Y-%m-%d)

GO_MODULE=	github.com/mgechev/${PORTNAME}
GO_BUILDFLAGS=	-ldflags "\
		-s -w \
		-X main.version=${_BUILD_VERSION} \
		-X main.commit=${_BUILD_COMMIT} \
		-X main.date=${_BUILD_DATE}"

PLIST_FILES=	bin/${PORTNAME}
PORTDOCS=	CODE_OF_CONDUCT.md CONTRIBUTING.md DEVELOPING.md \
		PULL_REQUEST_TEMPLATE.md README.md RULES_DESCRIPTIONS.md
PORTEXAMPLES=	defaults.toml untyped.toml

OPTIONS_DEFINE=	DOCS EXAMPLES

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S|^|${WRKSRC}/|} \
		${STAGEDIR}${DOCSDIR}

post-install-EXAMPLES-on:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${PORTEXAMPLES:S|^|${WRKSRC}/|} \
		${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>
