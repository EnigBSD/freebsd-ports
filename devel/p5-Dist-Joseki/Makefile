# Created by: Gea-Suan Lin <gslin@gslin.org>

PORTNAME=	Dist-Joseki
PORTVERSION=	0.20
PORTREVISION=	1
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Tools for the prolific module author

LICENSE=	ART10 GPLv1+
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-URI>=0:net/p5-URI \
		${RUN_DEPENDS}
RUN_DEPENDS=	p5-App-Cmd>=0:devel/p5-App-Cmd \
		p5-Class-Accessor-Complex>=0:devel/p5-Class-Accessor-Complex \
		p5-Data-Rmap>=0:devel/p5-Data-Rmap \
		p5-Error>=0:lang/p5-Error \
		p5-File-Slurp>=0:devel/p5-File-Slurp \
		p5-Getopt-Attribute>=0:devel/p5-Getopt-Attribute \
		p5-YAML>=0:textproc/p5-YAML

USES=		perl5
USE_PERL5=	configure

CONFLICTS_INSTALL=	ja-mh mmh nmh

NO_ARCH=	yes

.include <bsd.port.mk>
