PORTNAME=	HTTP-Exception
PORTVERSION=	0.04007
CATEGORIES=	www perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Perl extension to throw HTTP-Errors as (Exception::Class-) Exceptions

LICENSE=	ART10 GPLv1+
LICENSE_COMB=	dual

BUILD_DEPENDS=	${RUN_DEPENDS}
RUN_DEPENDS=	\
	p5-Exception-Class>=1.29:devel/p5-Exception-Class \
	p5-HTTP-Message>=5.817:www/p5-HTTP-Message
TEST_DEPENDS=	\
	p5-Test-Exception>=0.29:devel/p5-Test-Exception \
	p5-Test-NoWarnings>=1.04:devel/p5-Test-NoWarnings

USES=		perl5
USE_PERL5=	configure
NO_ARCH=	YES

.include <bsd.port.mk>
