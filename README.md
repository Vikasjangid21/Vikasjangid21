def sip_calculator(investment_amount, duration, expected_rate):
    """
    Calculates the returns on investment for a SIP (Systematic Investment Plan) in the stock market.
    
    Args:
        investment_amount (float): The monthly investment amount.
        duration (int): The duration of the SIP in months.
        expected_rate (float): The expected annual rate of return on investment.
        
    Returns:
        float: The total investment made and the final maturity amount.
    """
    total_investment = investment_amount * duration
    monthly_rate = (1 + expected_rate) ** (1/12) - 1
    
    maturity_amount = 0.0
    for month in range(1, duration + 1):
        monthly_investment = investment_amount * ((1 + monthly_rate) ** (duration - month + 1) - 1) / monthly_rate
        maturity_amount += monthly_investment
    
    return total_investment, maturity_amount


# Example usage
investment_amount = 5000  # Monthly investment amount
duration = 36  # Duration of SIP in months
expected_rate = 0.12  # Expected annual rate of return (12%)

total_investment, maturity_amount = sip_calculator(investment_amount, duration, expected_rate)

print(f"Total Investment: {total_investment:.2f}")
print(f"Maturity Amount: {maturity_amount:.2f}")
