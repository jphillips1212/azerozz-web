<template>
    <div class="grid">
      <div class="box" v-for="(boss, index) in bosses" :key="index">
        <boss-box 
        :name="boss.name" 
        :recorded_kills="boss.recorded_kills" 
        :guild_kills="boss.guild_kills" 
        :alliance_kills="boss.alliance_kills" 
        :horde_kills="boss.horde_kills"
        :tank_comp="boss.tank_comp"
        :healer_comp="boss.healer_comp" />
      </div>
    </div>
</template>

<style>
    .grid {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        grid-template-rows: repeat(2, minmax(0, 1fr));
        gap: 1px;
        max-width: 1500px;
        margin: 0 auto;
    }

    @media (max-width: 1400px) {
        .grid {
            grid-template-columns: repeat(2, minmax(0, 1fr));
            grid-template-rows: repeat(4, minmax(0, 1fr));
        }
    }

    @media (max-width: 700px) {
        .grid {
            grid-template-columns: minmax(0, 1fr);
            grid-template-rows: repeat(8, minmax(0, 1fr));
        }
}
</style>

<script>
import BossBox from './BossBox.vue';

export default {
    components: {
        BossBox
    },
    data() {
        return {
        bosses: [
            { name: 'Raszageth', recorded_kills: '156', guild_kills: '156', alliance_kills: '100', horde_kills: '100', 
            tank_comp: [
                { name: 'Protection Warrior' },
                { name: 'Havoc Demon Hunter'},
            ],
            healer_comp: [
                { name: 'Holy Paladin' },
                { name: 'Preservation Evoker' },
                { name: 'Holy Priest'},
                { name: 'Restoration Druid'},
            ]},
            { name: 'Broodkeeper Diurna', recorded_kills: '247', guild_kills: '244', alliance_kills: '64', horde_kills: '180', 
            tank_comp: [
                { name: 'Protection Paladin' },
                { name: 'Blood Death Knight'},
            ],
            healer_comp: [
                { name: 'Mistweaver Monk'},
                { name: 'Holy Paladin'},
                { name: 'Discipline Priest'},
                { name: 'Restoration Shaman'},
                { name: 'Holy Paladin'},
            ]},
            { name: 'Kurog Grimtotem', recorded_kills: '1054', guild_kills: '10027', alliance_kills: '9512', horde_kills: '515',
            tank_comp: [
                { name: 'Brewmaster Monk' },
                { name: 'Guardian Druid'},
            ],
            healer_comp: [
                { name: 'Mistweaver Monk'},
                { name: 'Holy Paladin'},
                { name: 'Holy Paladin'},
                { name: 'Holy Paladin'},
                { name: 'Discipline Priest'},
                { name: 'Restoration Shaman'},
                { name: 'Restoration Shaman'},
            ]},
            { name: 'Dathea', data: 'Data 4' },
            { name: 'Sennarth', data: 'Data 5' },
            { name: 'The Primal Council', data: 'Data 6' },
            { name: 'Terros', data: 'Data 7' },
            { name: 'Eranog', data: 'Data 8' },
        ]
        };
    },
};
</script>