# Created by: Emanuel Haupt <ehaupt@FreeBSD.org>

PORTNAME=	eden
PORTVERSION=	0.7.4
DISTVERSIONPREFIX=	v
PORTREVISION=	4
CATEGORIES=	www

PATCH_SITES=	https://github.com/${GH_ACCOUNT}/${GH_PROJECT}/commit/
PATCHFILES=	cffa0cee9f5897fbd96a3621f2c0dc8aeb90e711.patch:-p1

MAINTAINER=	ehaupt@FreeBSD.org
COMMENT=	Interact with any Open Service Broker API

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go:modules
USE_GITHUB=	yes

GH_ACCOUNT=	starkandwayne

GO_PKGNAME=	github.com/${GH_ACCOUNT}/${PORTNAME}

PLIST_FILES=	bin/eden

.include <bsd.port.mk>
