# Colour-harmony-generatorimport colorsys

def shift(h, deg):
    h = h.lstrip("#")
    r, g, b = (int(h[i:i+2], 16) / 255 for i in (0, 2, 4))
    hh, l, s = colorsys.rgb_to_hls(r, g, b)
    r, g, b = colorsys.hls_to_rgb((hh + deg / 360) % 1, l, s)
    return "#%02X%02X%02X" % (round(r * 255), round(g * 255), round(b * 255))

base = "#7B2FF7"
print("complementary", shift(base, 180))
print("triadic", shift(base, 120), shift(base, 240))
print("analogous", shift(base, -30), shift(base, 30))
