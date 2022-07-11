//Credit to LazyBear for some of his CVI code\\

study("Tops/Bottoms", shorttitle="Tops/Bottoms", overlay=true)
length=input(3)
ValC=sma(hl2, length)

bull=input(-.51, title="Bullish")
bear=input(.43, title="Bearish")
vol=sma(atr(length), length)
//filter=sma(cvi, 400)
// os2=input(-1.5, title="Oversold 2")
// ob2=input(1.5, title="Overbought 2")


cvi = (close-ValC) / (vol*sqrt(length))

plot(bull, color=green)
plot(bear, color=red)

// plot(os2, color=green, style=3)
// plot(ob2, color=red, style=3)
cb= cvi <= bull ? green : cvi >=bear ? red : cvi > bull ? blue : cvi < bear ? blue : na
bull1 = cvi <= bull
bear1 = cvi >= bear
bull2 = bull1[1] and not bull1
bear2 = bear1[1] and not bear1
plotchar(bull2, char="*", location=location.belowbar, color=lime, size=size.normal)
plotchar(bear2, char="*",  location=location.abovebar, color=red, size=size.normal)
//plotchar(bear1 ? cb : na)
//plot(cvi, color=cb, style=histogram, linewidth=2)
//plot(filter, color=red, linewidth=2)
