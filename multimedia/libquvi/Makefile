# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	libquvi
PORTVERSION=	0.4.1
PORTREVISION=	5
CATEGORIES=	multimedia devel
MASTER_SITES=	SF/quvi/${PORTVERSION:R}/libquvi/ \
		LOCAL/sunpoet

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Cross-platform library for parsing flash media stream URLs

LICENSE=	LGPL21+
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	${RUN_DEPENDS}
LIB_DEPENDS=	libcurl.so:ftp/curl
RUN_DEPENDS=	libquvi-scripts>=0.4.0:multimedia/libquvi-scripts

USES=		iconv libtool pathfix pkgconfig tar:xz

GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes

PORTDOCS=	*

PORTSCOUT=	limit:^0\.4\.

OPTIONS_DEFINE=	DOCS LUAJIT
LUAJIT_DESC=	Use LuaJIT instead of Lua

LUAJIT_LIB_DEPENDS=	libluajit-5.1.so:lang/luajit
LUAJIT_USES_OFF=	lua

post-patch-LUAJIT-off:
	@${REINPLACE_CMD} 's|lua-5.1|lua-${LUA_VER}|g' ${WRKSRC}/configure

post-patch-LUAJIT-on:
	@${REINPLACE_CMD} 's|lua >= 5.1|luajit|g' ${WRKSRC}/configure

post-install:
	${MKDIR} ${STAGEDIR}${DOCSDIR}/
	cd ${WRKSRC}/doc/nd/ && ${COPYTREE_SHARE} . ${STAGEDIR}${DOCSDIR}/

.include <bsd.port.mk>
