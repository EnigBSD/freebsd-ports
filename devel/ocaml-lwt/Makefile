# Created by: jaapb@kerguelen.org

PORTNAME=	lwt
PORTVERSION=	2.5.2
CATEGORIES=	devel
PKGNAMEPREFIX=	ocaml-

MAINTAINER=	danfe@FreeBSD.org
COMMENT=	Cooperative threading library for OCaml

LICENSE=	LGPL21

BUILD_DEPENDS=	${SA_DIR}/react/react.a:devel/ocaml-react \
		${SA_DIR}/ssl/ssl.a:security/ocaml-ssl
BUILD_DEPENDS+=	ocamlbuild:devel/ocaml-ocamlbuild
RUN_DEPENDS=	${SA_DIR}/react/react.a:devel/ocaml-react \
		${SA_DIR}/ssl/ssl.a:security/ocaml-ssl

USE_GITHUB=	yes
GH_ACCOUNT=	ocsigen

MAKE_JOBS_UNSAFE=	yes

USES=			gmake
USE_OCAML=		yes
OCAMLC_DEPEND=		ocaml>=3.11:${OCAMLC_PORT}
USE_OCAML_FINDLIB=	yes
USE_OCAML_CAMLP4=	yes
USE_OCAMLFIND_PLIST=	yes
USE_OCAML_LDCONFIG=	yes
HAS_CONFIGURE=		yes
CONFIGURE_ARGS=		--destdir "${STAGEDIR}" \
			--prefix "${PREFIX}" \
			--enable-camlp4 \
			--enable-ssl \
			--enable-react \
			--disable-libev \
			--disable-glib

DOCSDIR=		${PREFIX}/share/doc/ocaml/${PORTNAME}
SA_DIR=			${LOCALBASE}/${OCAML_SITELIBDIR}

OPTIONS_DEFINE=		DOCS

DOCS_CONFIGURE_ENABLE=	docs
DOCS_CONFIGURE_ON=	--docdir ${STAGEDIR}${DOCSDIR}
# For some reason, ocaml-text is needed when building documentation
DOCS_BUILD_DEPENDS=	${SA_DIR}/text/text.a:textproc/ocaml-text
DOCS_RUN_DEPENDS=	${SA_DIR}/text/text.a:textproc/ocaml-text

post-patch:
	@${REINPLACE_CMD} -e 's,"install" :: findlib_name,"install" :: "-destdir ${STAGEDIR}${PREFIX}/lib/ocaml/site-lib" :: "-ldconf /dev/null" :: findlib_name,' \
		${WRKSRC}/setup.ml
	@${REINPLACE_CMD} -e 's,| O_CLOEXEC,& | O_KEEPEXEC, \
	    ; s,else Unix\.socketpair ,&?cloexec:None,' \
		${WRKSRC}/src/unix/lwt_unix.ml \
		${WRKSRC}/src/unix/lwt_unix.mli
	@${REINPLACE_CMD} -e 's,socket -> string,socket -> bytes,' \
		${WRKSRC}/src/ssl/lwt_ssl.mli

do-configure:
	cd ${WRKSRC}; ocaml setup.ml -configure ${CONFIGURE_ARGS}
	@${REINPLACE_CMD} -e 's%"-lev"%"-lev -L${PREFIX}/lib/ev -Wl,-R${PREFIX}/lib/ev"%' \
		${WRKSRC}/setup.data

do-build:
	cd ${WRKSRC}; ocaml setup.ml -build

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${OCAML_SITELIBDIR}
	cd ${WRKSRC}; ocaml setup.ml -install

.include <bsd.port.mk>
