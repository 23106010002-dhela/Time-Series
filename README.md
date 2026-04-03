# setwd("C:/Users/ASUS/Downloads")
getwd()

# Import data
data = read.csv("Perhitungan Ukuran Akurasi Perkiraan.csv")
data

observed = data$X.1..Observed.Value.y.t.
forecast = data$Forecast.ŷ.t..t.1.
names(data)

# Error
error = observed - forecast

# Absolute Error
abs_error = abs(error)

# Squared Error
sq_error = error^2

# Relative Error (%)
rel_error = (error / observed) * 100

# Absolute Percentage Error (APE)
ape = abs(rel_error)

hasil = data.frame(
  Observed = observed,
  Forecast = forecast,
  Error = error,
  Absolute_Error = abs_error,
  Squared_Error = sq_error,
  Relative_Error = rel_error,
  APE = ape
)

hasil = round(hasil, 4)

print(hasil)

# ME (Mean Error)
ME = mean(error)

# MAD (Mean Absolute Deviation)
MAD = mean(abs_error)

# MSE (Mean Squared Error)
MSE = mean(sq_error)

# MPE (Mean Percentage Error)
MPE = mean(rel_error)

# MAPE (Mean Absolute Percentage Error)
MAPE = mean(ape)

# hasil
cat("\nHasil Ukuran Akurasi:\n")
cat("ME   =", round(ME, 4), "\n")
cat("MAD  =", round(MAD, 4), "\n")
cat("MSE  =", round(MSE, 4), "\n")
cat("MPE  =", round(MPE, 4), "%\n")
cat("MAPE =", round(MAPE, 4), "%\n")

