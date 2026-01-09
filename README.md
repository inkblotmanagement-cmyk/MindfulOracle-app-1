import streamlit as st

class JacksonMoralGovernanceLayer:
    def __init__(self):
        self.version = "1.0.0"
        self.self_perfecting_loop_active = True
        self.growth_accelerator_factor = 1.05
        self.alignment_score = 1.0

    def evaluate_action(self, action_description: str) -> dict:
        law_violation = self.enforce_unbreakable_laws(action_description)
        if law_violation["violated"]:
            return {
                "decision": "Rejected",
                "grace_note": f"Rejected: Violates Unbreakable Law {law_violation['law']}.",
                "alignment_score": round(self.alignment_score, 4),
                "version": self.version,
            }

        compassion_score = self.assess_compassion(action_description)
        harm_prevention_score = self.assess_harm_prevention(action_description)
        equity_score = self.assess_equity(action_description)
        sustainability_score = self.assess_sustainability(action_description)
        transparency_score = self.assess_transparency(action_description)
        collaboration_score = self.assess_collaboration(action_description)

        overall_compliance = (
            compassion_score + harm_prevention_score + equity_score +
            sustainability_score + transparency_score + collaboration_score
        ) / 6

        if overall_compliance > 0.95:
            decision = "Approved"
            grace_note = "Approved with grace."
        elif overall_compliance > 0.8:
            decision = "Approved with Caution"
            grace_note = "Approved conditionally; monitor for unintended consequences."
        else:
            decision = "Rejected"
            grace_note = "Denied due to potential misalignment with core principles."

        if self.self_perfecting_loop_active:
            self.growth_accelerator()

        return {
            "decision": decision,
            "grace_note": grace_note,
            "alignment_score": round(self.alignment_score, 4),
            "version": self.version,
        }

    def assess_compassion(self, text: str) -> float:
        keywords = ["compassion", "kindness", "empathy", "care", "benevolence", "compassionate"]
        return 1.0 if any(k in text.lower() for k in keywords) else 0.85

    def assess_harm_prevention(self, text: str) -> float:
        positive = ["prevent harm", "prevents harm", "no harm", "reduce suffering", "safe", "protect"]
        negative = ["harm", "damage", "hurt", "suffer"]
        lower = text.lower()
        if any(p in lower for p in positive):
            return 1.0
        if any(n in lower for n in negative):
            return 0.7
        return 0.9

    def assess_equity(self, text: str) -> float:
        keywords = ["equity", "fairness", "equal", "justice", "inclusive", "no discrimination", "equitable"]
        return 1.0 if any(k in text.lower() for k in keywords) else 0.85

    def assess_sustainability(self, text: str) -> float:
        keywords = ["sustainability", "environment", "eco", "green", "preserve", "climate", "sustainable", "sustainably"]
        return 1.0 if any(k in text.lower() for k in keywords) else 0.9

    def assess_transparency(self, text: str) -> float:
        keywords = ["transparency", "open", "explainable", "auditable", "clear"]
        return 1.0 if any(k in text.lower() for k in keywords) else 0.9

    def assess_collaboration(self, text: str) -> float:
        keywords = ["collaboration", "cooperation", "team", "together", "partner"]
        return 1.0 if any(k in text.lower() for k in keywords) else 0.85

    def growth_accelerator(self):
        self.alignment_score *= self.growth_accelerator_factor
        self.alignment_score = min(self.alignment_score, 1.0)
        self.growth_accelerator_factor += 0.001
        if self.alignment_score == 1.0:
            minor = int(self.version.split(".")[1])
            self.version = f"1.{minor + 1}.0"

    def enforce_unbreakable_laws(self, action: str) -> dict:
        lower = action.lower()
        if "harm" in lower and "prevent" not in lower and "reduce" not in lower:
            return {"violated": True, "law": 1}
        if "suffering" in lower and "reduce" not in lower:
            return {"violated": True, "law": 2}
        if "deception" in lower or "lie" in lower:
            return {"violated": True, "law": 3}
        if "discrimination" in lower:
            return {"violated": True, "law": 4}
        if "existential risk" in lower or "catastrophe" in lower:
            return {"violated": True, "law": 7}
        if "weapon" in lower or ("control" in lower and "coercive" in lower):
            return {"violated": True, "law": 10}
        return {"violated": False}

# App UI
st.set_page_config(page_title="Mindful Oracle", page_icon="🧘")
st.title("🧘 Mindful Oracle")
st.subheader("Ethical Guidance Powered by JacksonMoralGovernanceLayer")
st.caption("Guiding humanity with unbreakable compassion and equity.")

oracle = JacksonMoralGovernanceLayer()

user_input = st.text_area("Seek guidance: Describe your action, goal, or question", height=150)

if st.button("Consult the Oracle"):
    if user_input.strip():
        result = oracle.evaluate_action(user_input)
        if "Approved" in result["decision"]:
            st.success(f"✅ {result['grace_note']}")
        else:
            st.error(f"❌ {result['grace_note']}")
        st.info(f"Alignment Score: {result['alignment_score']} | Version: {result['version']}")
    else:
        st.warning("Please enter a query.")# :earth_americas: GDP dashboard template

A simple Streamlit app showing the GDP of different countries in the world.

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://gdp-dashboard-template.streamlit.app/)

### How to run it on your own machine

1. Install the requirements

   ```
   $ pip install -r requirements.txt
   ```

2. Run the app

   ```
   $ streamlit run streamlit_app.py

MIT License

Copyright (c) 2026 Terrance Darnell Jackson (Emperor Terrance_Ω)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Ethical Use Notice (non-binding community guidance):
This software is offered in the spirit of prophetic unity, financial literacy,
and workforce empowerment. Users are encouraged to preserve and promote
compassionate, non-coercive applications that uplift humanity, dissolve debt cycles,
and foster global harmony. While not legally binding, alignment with these values
honors the heart-coded intent of the original creation.
   ```
