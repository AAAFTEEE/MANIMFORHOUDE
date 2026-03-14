# 代码大部分都是豆包 AI 生的，AAAFTEEE 修改了一部分。
from manim import *

# ========== 1. 定义元素类别颜色（化学规范配色） ==========
COLOR_MAP = {
    # 碱金属
    "alkali_metal": rgb_to_color((0.95, 0.4, 0.4)),    # 浅红
    # 碱土金属
    "alkaline_earth_metal": rgb_to_color((0.95, 0.7, 0.4)),  # 浅橙
    # 过渡金属
    "transition_metal": rgb_to_color((0.4, 0.7, 0.95)),  # 浅蓝
    # 镧系
    "lanthanide": rgb_to_color((0.7, 0.4, 0.95)),       # 浅紫
    # 锕系
    "actinide": rgb_to_color((0.9, 0.4, 0.9)),          # 浅粉紫
    # 主族金属
    "main_group_metal": rgb_to_color((0.4, 0.95, 0.7)),  # 浅绿
    # 非金属
    "nonmetal": rgb_to_color((0.7, 0.95, 0.4)),         # 浅黄绿
    # 卤素
    "halogen": rgb_to_color((0.95, 0.9, 0.4)),          # 浅黄
    # 稀有气体
    "noble_gas": rgb_to_color((0.95, 0.4, 0.8)),        # 浅粉
    # 其他金属
    "other_metal": rgb_to_color((0.4, 0.95, 0.95)),     # 浅青
    # 类金属
    "metalloid": rgb_to_color((0.6, 0.8, 0.6)),         # 浅草绿
}

# ========== 2. 元素信息 + 类别标注（核心） ==========
elements_info = {
    # 原子序数: (中文名称, 英文符号, 元素类别)
    1: ("氢", "H", "nonmetal"), 2: ("氦", "He", "noble_gas"),
    3: ("锂", "Li", "alkali_metal"), 4: ("铍", "Be", "alkaline_earth_metal"), 
    5: ("硼", "B", "metalloid"), 6: ("碳", "C", "nonmetal"), 7: ("氮", "N", "nonmetal"), 
    8: ("氧", "O", "nonmetal"), 9: ("氟", "F", "halogen"), 10: ("氖", "Ne", "noble_gas"),
    11: ("钠", "Na", "alkali_metal"), 12: ("镁", "Mg", "alkaline_earth_metal"), 
    13: ("铝", "Al", "main_group_metal"), 14: ("硅", "Si", "metalloid"), 15: ("磷", "P", "nonmetal"), 
    16: ("硫", "S", "nonmetal"), 17: ("氯", "Cl", "halogen"), 18: ("氩", "Ar", "noble_gas"),
    19: ("钾", "K", "alkali_metal"), 20: ("钙", "Ca", "alkaline_earth_metal"), 
    21: ("钪", "Sc", "transition_metal"), 22: ("钛", "Ti", "transition_metal"), 23: ("钒", "V", "transition_metal"), 
    24: ("铬", "Cr", "transition_metal"), 25: ("锰", "Mn", "transition_metal"), 26: ("铁", "Fe", "transition_metal"), 
    27: ("钴", "Co", "transition_metal"), 28: ("镍", "Ni", "transition_metal"), 29: ("铜", "Cu", "transition_metal"), 
    30: ("锌", "Zn", "transition_metal"), 31: ("镓", "Ga", "main_group_metal"), 32: ("锗", "Ge", "metalloid"), 
    33: ("砷", "As", "metalloid"), 34: ("硒", "Se", "nonmetal"), 35: ("溴", "Br", "halogen"), 36: ("氪", "Kr", "noble_gas"),
    37: ("铷", "Rb", "alkali_metal"), 38: ("锶", "Sr", "alkaline_earth_metal"), 
    39: ("钇", "Y", "transition_metal"), 40: ("锆", "Zr", "transition_metal"), 41: ("铌", "Nb", "transition_metal"), 
    42: ("钼", "Mo", "transition_metal"), 43: ("锝", "Tc", "transition_metal"), 44: ("钌", "Ru", "transition_metal"), 
    45: ("铑", "Rh", "transition_metal"), 46: ("钯", "Pd", "transition_metal"), 47: ("银", "Ag", "transition_metal"), 
    48: ("镉", "Cd", "transition_metal"), 49: ("铟", "In", "main_group_metal"), 50: ("锡", "Sn", "main_group_metal"), 
    51: ("锑", "Sb", "metalloid"), 52: ("碲", "Te", "metalloid"), 53: ("碘", "I", "halogen"), 54: ("氙", "Xe", "noble_gas"),
    55: ("铯", "Cs", "alkali_metal"), 56: ("钡", "Ba", "alkaline_earth_metal"), 
    57: ("镧", "La", "lanthanide"), 58: ("铈", "Ce", "lanthanide"), 59: ("镨", "Pr", "lanthanide"), 
    60: ("钕", "Nd", "lanthanide"), 61: ("钷", "Pm", "lanthanide"), 62: ("钐", "Sm", "lanthanide"), 
    63: ("铕", "Eu", "lanthanide"), 64: ("钆", "Gd", "lanthanide"), 65: ("铽", "Tb", "lanthanide"), 
    66: ("镝", "Dy", "lanthanide"), 67: ("钬", "Ho", "lanthanide"), 68: ("铒", "Er", "lanthanide"), 
    69: ("铥", "Tm", "lanthanide"), 70: ("镱", "Yb", "lanthanide"), 71: ("镥", "Lu", "lanthanide"), 
    72: ("铪", "Hf", "transition_metal"), 73: ("钽", "Ta", "transition_metal"), 74: ("钨", "W", "transition_metal"), 
    75: ("铼", "Re", "transition_metal"), 76: ("锇", "Os", "transition_metal"), 77: ("铱", "Ir", "transition_metal"), 
    78: ("铂", "Pt", "transition_metal"), 79: ("金", "Au", "transition_metal"), 80: ("汞", "Hg", "transition_metal"), 
    81: ("铊", "Tl", "main_group_metal"), 82: ("铅", "Pb", "main_group_metal"), 83: ("铋", "Bi", "main_group_metal"), 
    84: ("钋", "Po", "metalloid"), 85: ("砹", "At", "halogen"), 86: ("氡", "Rn", "noble_gas"),
    87: ("钫", "Fr", "alkali_metal"), 88: ("镭", "Ra", "alkaline_earth_metal"), 
    89: ("锕", "Ac", "actinide"), 90: ("钍", "Th", "actinide"), 91: ("镤", "Pa", "actinide"), 
    92: ("铀", "U", "actinide"), 93: ("镎", "Np", "actinide"), 94: ("钚", "Pu", "actinide"), 
    95: ("镅", "Am", "actinide"), 96: ("锔", "Cm", "actinide"), 97: ("锫", "Bk", "actinide"), 
    98: ("锎", "Cf", "actinide"), 99: ("锿", "Es", "actinide"), 100: ("镄", "Fm", "actinide"), 
    101: ("钔", "Md", "actinide"), 102: ("锘", "No", "actinide"), 103: ("铹", "Lr", "actinide"), 
    104: ("𬬻", "Rf", "transition_metal"), 105: ("𬭊", "Db", "transition_metal"), 106: ("𬭳", "Sg", "transition_metal"), 
    107: ("𬭛", "Bh", "transition_metal"), 108: ("𬭶", "Hs", "transition_metal"), 109: ("鿏", "Mt", "transition_metal"), 
    110: ("𫟼", "Ds", "transition_metal"), 111: ("𬬭", "Rg", "transition_metal"), 112: ("鎶", "Cn", "transition_metal"), 
    113: ("鉨", "Nh", "main_group_metal"), 114: ("𫓧", "Fl", "main_group_metal"), 115: ("镆", "Mc", "main_group_metal"), 
    116: ("鉝", "Lv", "main_group_metal"), 117: ("鿬", "Ts", "halogen"), 118: ("鿫", "Og", "noble_gas")
}

# ========== 3. 按系分组（动画逻辑） ==========
groups = [
    [1, 2],
    [3,4,5,6,7,8,9,10],
    [11,12,13,14,15,16,17,18],
    [19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36],
    [37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54],
    [55,56,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86],
    [87,88,104,105,106,107,108,109,110,111,112,113,114,115,116,117,118],
    [57,58,59,60,61,62,63,64,65,66,67,68,69,70,71],
    [89,90,91,92,93,94,95,96,97,98,99,100,101,102,103]
]

# ========== 4. 位置映射（居中不溢出） ==========
positions = {
    1: (0,0), 2: (0,17),
    3: (1,0), 4: (1,1), 5: (1,12), 6: (1,13), 7: (1,14), 8: (1,15), 9: (1,16), 10: (1,17),
    11:(2,0),12:(2,1),13:(2,12),14:(2,13),15:(2,14),16:(2,15),17:(2,16),18:(2,17),
    19:(3,0),20:(3,1),21:(3,2),22:(3,3),23:(3,4),24:(3,5),25:(3,6),26:(3,7),27:(3,8),28:(3,9),29:(3,10),30:(3,11),31:(3,12),32:(3,13),33:(3,14),34:(3,15),35:(3,16),36:(3,17),
    37:(4,0),38:(4,1),39:(4,2),40:(4,3),41:(4,4),42:(4,5),43:(4,6),44:(4,7),45:(4,8),46:(4,9),47:(4,10),48:(4,11),49:(4,12),50:(4,13),51:(4,14),52:(4,15),53:(4,16),54:(4,17),
    55:(5,0),56:(5,1),72:(5,3),73:(5,4),74:(5,5),75:(5,6),76:(5,7),77:(5,8),78:(5,9),79:(5,10),80:(5,11),81:(5,12),82:(5,13),83:(5,14),84:(5,15),85:(5,16),86:(5,17),
    87:(6,0),88:(6,1),104:(6,3),105:(6,4),106:(6,5),107:(6,6),108:(6,7),109:(6,8),110:(6,9),111:(6,10),112:(6,11),113:(6,12),114:(6,13),115:(6,14),116:(6,15),117:(6,16),118:(6,17),
    57:(7,2),58:(7,3),59:(7,4),60:(7,5),61:(7,6),62:(7,7),63:(7,8),64:(7,9),65:(7,10),66:(7,11),67:(7,12),68:(7,13),69:(7,14),70:(7,15),71:(7,16),
    89:(8,2),90:(8,3),91:(8,4),92:(8,5),93:(8,6),94:(8,7),95:(8,8),96:(8,9),97:(8,10),98:(8,11),99:(8,12),100:(8,13),101:(8,14),102:(8,15),103:(8,16),
}

class PeriodicTable(Scene):
    def construct(self):
        # ========== 基础配置 ==========
        CHINESE_FONT = "SimSun"  # Windows必装宋体，中文100%显示
        CELL_WIDTH = 0.7
        CELL_HEIGHT = 0.8
        GAP = 0.05
        element_cells = {}

        # ========== 生成彩色元素格子 ==========
        for atomic_num, (cn_name, en_sym, elem_type) in elements_info.items():
            if atomic_num not in positions:
                continue
            
            # 获取位置
            row, col = positions[atomic_num]
            # 获取对应类别颜色
            cell_color = COLOR_MAP.get(elem_type, WHITE)

            # 1. 彩色背景框（核心：按类别填色）
            cell_rect = Rectangle(
                width=CELL_WIDTH, height=CELL_HEIGHT,
                stroke_width=1, stroke_color=WHITE, 
                fill_color=cell_color, fill_opacity=0.6  # 半透明填充，文字更清晰
            )

            # 2. 文字部分（对比色，确保醒目）
            # 原子序数（左上）
            num_text = Text(
                str(atomic_num),
                font=CHINESE_FONT,
                font_size=14,
                color=BLACK  # 黑色文字，彩色背景更醒目
            )
            # 中文名称（居中，最大）
            cn_text = Text(
                cn_name,
                font=CHINESE_FONT,
                font_size=24,
                color=BLACK
            )
            # 英文符号（中文下方）
            en_text = Text(
                en_sym,
                font=CHINESE_FONT,
                font_size=14,
                color=BLACK
            )

            # 3. 排版对齐
            num_text.move_to(cell_rect.get_corner(UL) + np.array([0.12, -0.1, 0]))
            cn_text.move_to(cell_rect.get_center())
            en_text.move_to(cell_rect.get_center() + np.array([0, -0.25, 0]))

            # 4. 定位格子
            x = col * (CELL_WIDTH + GAP)
            y = -row * (CELL_HEIGHT + GAP)
            cell_group = VGroup(cell_rect, num_text, cn_text, en_text)
            cell_group.move_to(np.array([x, y, 0]))
            element_cells[atomic_num] = cell_group

        # ========== 整体调整（居中+缩放） ==========
        full_table = VGroup(*element_cells.values())
        full_table.scale(0.55).move_to(ORIGIN)

        # ========== 核心动画：按系画框→写字 ==========
        for group in groups:
            current_rects = VGroup(*[element_cells[num][0] for num in group if num in element_cells])
            current_texts = VGroup(*[element_cells[num][1:] for num in group if num in element_cells])
            self.play(Create(current_rects), run_time=0.6)
            self.play(FadeIn(current_texts), run_time=0.6)
            self.wait(0.2)

        # 最后停留3秒
        self.wait(3)
