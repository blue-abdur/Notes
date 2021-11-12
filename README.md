# notes
séance bootstrap

oad("C:/Users/falis/desktop/dataAQR")

mod <- glm((dep.cons==1)~age+wais+rd, data=mhp, family=binomial)

summary(mod)


rlmhp <- function(data, index)

{

ds <- data[index,]

mod <- glm((dep.cons==1)~age+wais+rd, data=ds, family="binomial")

coefficients(mod)[3]

}

library(boot)

resboot <- boot(mhp, rlmhp, 10000)

hist(resboot$t, breaks=100)


quantile(resboot$t, probs=c(0.025, 0.975))
