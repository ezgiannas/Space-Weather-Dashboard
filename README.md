import streamlit as st
import plotly.graph_objs as go

# Set page config
st.set_page_config(layout="wide", page_title="Solar Storm Power Grid Monitoring")

# --- Header ---
st.markdown("""
    <h2 style='text-align: center; color: white;'>SOLAR STORM – POWER GRID MONITORING</h2>
""", unsafe_allow_html=True)

# --- Top Row: Storm Info | Map | Recommendations ---
top_col1, top_col2, top_col3 = st.columns([1.5, 2.5, 1.5])

with top_col1:
    st.markdown("### SOLAR STORM (G3 STRONG)")
    st.write("**Kp index:** 7")
    st.write("**Expected:** 8:00 PM – 3:00 AM")
    st.write("**Solar wind speed:** 709 km/s")
    st.write("**Density:** 18.5 p/cm³")
    st.write("**Bz:** -15 nT")
    st.markdown("<span style='color:orange; font-weight:bold;'>ALERT</span>", unsafe_allow_html=True)

with top_col2:
    st.image("dashboard_map.png", caption="Map of power grid risk levels")

with top_col3:
    st.markdown("### OPERATIONAL RECOMMENDATIONS")
    st.markdown("- Reduce loading on high-risk transformers")
    st.markdown("- Adjust transformer taps to limit GIC")
    st.markdown("- Consider delaying planned maintenance")

# --- Middle Row: GIC + Voltage Stability ---
middle_col1, middle_col2 = st.columns(2)

gic_fig = go.Figure()
gic_fig.add_trace(go.Scatter(y=[30, 32, 33, 34, 36, 40, 42, 47, 52, 60, 65, 70], mode='lines', line=dict(color='orange')))
gic_fig.update_layout(title='Transformer GIC', paper_bgcolor='#0e1117', plot_bgcolor='#0e1117', font=dict(color='white'))

voltage_fig = go.Figure()
voltage_fig.add_trace(go.Scatter(y=[0.98, 0.97, 0.965, 0.95, 0.955, 0.96, 0.955, 0.96, 0.95, 0.94, 0.93, 0.92], mode='lines', line=dict(color='orange')))
voltage_fig.update_layout(title='Voltage Stability', paper_bgcolor='#0e1117', plot_bgcolor='#0e1117', font=dict(color='white'))

middle_col1.plotly_chart(gic_fig, use_container_width=True)
middle_col2.plotly_chart(voltage_fig, use_container_width=True)

# --- Bottom Row: Risk Levels + Substation Status ---
bottom_col1, bottom_col2 = st.columns(2)

risk_fig = go.Figure()
risk_fig.add_trace(go.Pie(labels=['High', 'Medium', 'Low'], values=[28, 41, 31],
                          marker=dict(colors=['#d9534f', '#f0ad4e', '#5cb85c']), hole=0.4))
risk_fig.update_layout(title='Risk Levels', paper_bgcolor='#0e1117', font=dict(color='white'))

bottom_col1.plotly_chart(risk_fig, use_container_width=True)

with bottom_col2:
    st.markdown("### SUBSTATION STATUS")
    st.write("**Gridport Sub:** High")
    st.write("**Maple Sub 85:** Trap rot: 134 °F")
    st.write("**Elmwood Sub 43:** GIC 63 A")
