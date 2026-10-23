
<template>
    <section id="partnerships">
        <h3>Partners and Memberships</h3>
        <div class="row">
            <div class="top">
            <div class="partnerships-card">
            <img src="@/assets/oracle.png" class="oracle">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/cisco.png" class="cisco">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/acer.jpg" class="acer">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/huawei.jpg" class="huawei">
            </div>
        </div>
        
        <div class="bottom">
            <div class="partnerships-card">
            <img src="@/assets/psite.png" class="psite">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/govesmart.jpg" class="govesmart">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/mayad.png" class="mayad">
            </div>
            <div class="partnerships-card">
                <img src="@/assets/lasortech.jpg" class="lasortech">
            </div>
        </div>
        </div>
    </section>
</template>

<style>
#partnerships h3{
    justify-self: center;
    font-family: 'Times New Roman', Times, serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: #2b1b53;
}

#partnerships {
    justify-self: center;
    min-height: 50vh;
}

.top {
    display: flex;
    gap: 2rem;
    margin-bottom: 2rem;

}
.bottom {
    display: flex;
}


</style>